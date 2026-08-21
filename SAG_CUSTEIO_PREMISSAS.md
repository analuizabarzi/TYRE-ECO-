# SAG Ambiental — Premissas de custeio fabril

**Documento para validação do engenheiro de produção**

Objetivo: confirmar se o fluxo da linha, os rendimentos e a forma de ratear custos batem com a operação real da planta de trituração de pneus.

| Item | Valor |
|---|---|
| Painel | https://tyre-eco.web.app/sag_ambiental.html |
| Arquivo | `sag_ambiental.html` |
| Versão do modelo | v1 (rateio Aluguel + Outros) |
| Público | Engenharia de produção / PCP / custos |

> Marque cada premissa como **OK**, **Ajustar** ou **Não se aplica**. Onde for **Ajustar**, escreva o valor ou regra correta.

---

## 1. O que o painel calcula

Dado o volume lançado no período + custos + preços, o painel estima:

1. Quantas toneladas passam em cada equipamento
2. Quais produtos saem e em que quantidade
3. Custo unitário (R$/t) de cada saída
4. Margem potencial (preço − custo) × quantidade

Não substitui ERP. É um modelo de custeio de linha para simular margem.

---

## 2. Fluxo físico modelado

```
Matéria-prima
     │
     ▼
 [ Descarga ]  ← toda entrada passa aqui
     │
     ├── pneu de carga ──────────► [ Destalonador ]
     │                                  │
     │                         30% ► Aço Sujo (venda)
     │                         70% ► [ Trit. Primária ] ──► chip ──► [ Trit. Secundária ]
     │
     ├── pneu de passeio ───────► [ Trit. Primária ] ──► Chip (venda)  ✗ não vai à secundária
     │
     └── chip comprado ─────────► (após Descarga) ──────────────────► [ Trit. Secundária ]
                                                                              │
                                                              ┌───────────────┼───────────────┐
                                                              ▼               ▼               ▼
                                                         Aço Limpo        Mesh 10/20/30
```

### Premissas de roteamento (fixas no sistema)

| # | Premissa atual | OK / Ajustar / N/A | Correção sugerida |
|---|---|---|---|
| R1 | **Toda** matéria-prima passa por Descarga | | |
| R2 | Só **pneu de carga** passa pelo Destalonador | | |
| R3 | No Destalonador: **30%** vira Aço Sujo e **70%** segue para Trit. Primária | | |
| R4 | Os **70%** do pneu de carga, após Primária, viram chip 100% e vão para Secundária | | |
| R5 | **Pneu de passeio** vai direto para Trit. Primária (sem Destalonador) | | |
| R6 | Chip do pneu de passeio é **produto final de venda** e **não** entra na Secundária | | |
| R7 | **Chip comprado** não passa por Destalonador nem Primária; entra na Secundária | | |
| R8 | Chip comprado ainda “conta” tonelagem em Descarga (custo de descarga é rateado nele) | | |

---

## 3. Equipamentos / processos

| Processo | O que recebe (modelo atual) |
|---|---|
| Descarga | Soma de todas as toneladas lançadas |
| Destalonador | Só pneu de carga |
| Trituração Primária | 70% do pneu de carga + 100% do pneu de passeio |
| Trituração Secundária | Chip gerado da carga (70%) + chip comprado |

| # | Premissa | OK / Ajustar / N/A | Correção |
|---|---|---|---|
| E1 | A linha tem exatamente esses 4 processos | | |
| E2 | Não há processo intermediário omitido (ex.: peneira, magnetismo extra, silo) | | |
| E3 | Perdas / rejeito / umidade **não** estão modelados (tudo que entra vira saída útil) | | |

---

## 4. Saídas (produtos) e rendimentos

### 4.1 Saídas da linha

| Produto | Origem no modelo |
|---|---|
| Aço Sujo | Destalonador (30% do pneu de carga) |
| Chip (venda) | Trit. Primária a partir do pneu de passeio |
| Aço Limpo | Trit. Secundária |
| Mesh 10 | Trit. Secundária |
| Mesh 20 | Trit. Secundária |
| Mesh 30 | Trit. Secundária |

### 4.2 Rendimento da Trituração Secundária (editável no painel)

Valores **placeholder** atuais (devem fechar 100%):

| Saída | % atual (placeholder) | % real da planta | OK / Ajustar |
|---|---|---|---|
| Aço Limpo | 5% | | |
| Mesh 10 | 30% | | |
| Mesh 20 | 35% | | |
| Mesh 30 | 30% | | |
| **Soma** | **100%** | | |

| # | Premissa | OK / Ajustar / N/A | Correção |
|---|---|---|---|
| Y1 | Secundária só gera essas 4 saídas (sem fibra, rejete, pó, etc.) | | |
| Y2 | O rendimento é em **% mássica** sobre a tonelada de chip que entra | | |
| Y3 | Não há diferença de rendimento entre chip de carga e chip comprado | | |

---

## 5. Estrutura de custos

### 5.1 Custos diretos por equipamento (R$/período)

Em cada processo o usuário informa:

- Mão de obra
- Energia
- Manutenção
- Depreciação
- Insumos

**Total direto do equipamento** = soma das 5 categorias.

| # | Premissa | OK / Ajustar / N/A | Correção |
|---|---|---|---|
| C1 | Essas 5 categorias cobrem o custo direto de cada máquina | | |
| C2 | Mão de obra fica **só** no direto (não há rateio separado de “funcionários”) | | |
| C3 | Custos são informados no **mesmo período** dos lançamentos de produção | | |

### 5.2 Custos indiretos rateados (R$/período)

Informados uma vez para a planta e rateados nos 4 equipamentos:

- Aluguel
- Outros

**% de rateio padrão:** 25% / 25% / 25% / 25% (editável; deve somar 100%).

```
Rateio no equipamento = (Aluguel + Outros) × (% do equipamento)
Total do equipamento  = Custos diretos + Rateio
Custo/t do equipamento = Total ÷ toneladas que passaram no equipamento no período
```

| # | Premissa | OK / Ajustar / N/A | Correção |
|---|---|---|---|
| I1 | Aluguel e Outros devem ser rateados nos 4 equipamentos | | |
| I2 | Rateio por **% fixo** (e não por tonelada, hora-máquina, kWh, etc.) é aceitável | | |
| I3 | % padrão 25/25/25/25 faz sentido como ponto de partida | | |
| I4 | Se um equipamento processar 0 t no período, o rateio ainda cai nele (fica no total, mas custo/t = 0) | | |

---

## 6. Como o custo chega em cada produto (R$/t)

### 6.1 Aquisição de matéria-prima (R$/t, editável)

- Pneu de carga
- Pneu de passeio
- Chip comprado

### 6.2 Fórmulas atuais de custo unitário

| Produto | Fórmula de custo/t usada hoje |
|---|---|
| **Aço Sujo** | Aquisição pneu carga + Custo/t Descarga + Custo/t Destalonador |
| **Chip (venda)** (passeio) | Aquisição pneu passeio + Custo/t Descarga + Custo/t Primária |
| **Aço Limpo / Mesh 10 / 20 / 30** | Custo médio de entrada na Secundária + Custo/t Secundária |

**Custo do chip de carga até a entrada da Secundária:**

```
Aquisição pneu carga
+ Custo/t Descarga
+ Custo/t Destalonador ÷ 0,7
+ Custo/t Primária
```

O ÷ 0,7 concentra o custo do Destalonador na fração que segue (70%).

**Chip comprado até a Secundária:**

```
Custo/t Descarga + Aquisição chip comprado
```

**Entrada média na Secundária:** média ponderada entre chip de carga e chip comprado.

| # | Premissa | OK / Ajustar / N/A | Correção |
|---|---|---|---|
| K1 | Aço Sujo **leva** custo de Descarga + Destalonador (e aquisição do pneu carga) | | |
| K2 | Aço Sujo **não** leva custo de Primária nem Secundária | | |
| K3 | Dividir o Destalonador por 0,7 no caminho do chip está correto | | |
| K4 | Chip de passeio **não** carrega Destalonador nem Secundária | | |
| K5 | Aço Limpo e os 3 Meshes têm **o mesmo** custo/t (sem diferenciação por produto) | | |
| K6 | Aquisição de matéria-prima entra no custo unitário (mass-alocada) | | |

---

## 7. Preços de venda (editáveis)

Defaults atuais no painel (só referência; validar com comercial):

| Produto | Preço default (R$/t) | Preço real | OK / Ajustar |
|---|---|---|---|
| Aço Sujo | 300 | | |
| Aço Limpo | 500 | | |
| Chip (venda) | 650 | | |
| Mesh 10 | 1.800 | | |
| Mesh 20 | 2.000 | | |
| Mesh 30 | 2.200 | | |

Margem = (Preço − Custo/t) × Quantidade.

---

## 8. Exemplo numérico rápido (para checagem)

Lançamento padrão do painel:

| Matéria-prima | Ton |
|---|---|
| Pneu de carga | 100 |
| Pneu de passeio | 60 |
| Chip comprado | 40 |

Resultado esperado do fluxo (com as premissas atuais):

| Ponto | Ton |
|---|---|
| Descarga | 200 |
| Destalonador | 100 |
| Aço Sujo | 30 |
| Trit. Primária | 130 (= 70 + 60) |
| Chip venda (passeio) | 60 |
| Trit. Secundária | 110 (= 70 + 40) |
| Aço Limpo (5%) | 5,5 |
| Mesh 10 (30%) | 33,0 |
| Mesh 20 (35%) | 38,5 |
| Mesh 30 (30%) | 33,0 |

| # | Checagem | OK / Ajustar | Observação |
|---|---|---|---|
| X1 | Esses tonelagens batem com o balanço de massa real da planta? | | |

---

## 9. O que o modelo **não** faz ainda

Confirmar se algum destes pontos é obrigatório para a v1:

| # | Lacuna | Precisa na v1? (S/N) | Como deveria funcionar |
|---|---|---|---|
| L1 | Perdas / rejeito / umidade | | |
| L2 | Capacidade (t/h) e gargalo de linha | | |
| L3 | Estoque intermediário (WIP) | | |
| L4 | Custo diferente por Mesh (hoje todos iguais) | | |
| L5 | Rateio por hora-máquina / kWh em vez de % | | |
| L6 | Frete de entrada/saída | | |
| L7 | Impostos na margem | | |
| L8 | Múltiplos turnos / setup / ociosidade | | |

---

## 10. Parecer do engenheiro de produção

**Responsável:** _______________________________  
**Data:** ____/____/________  
**Planta / linha:** _______________________________

### Resultado

- [ ] Premissas **aprovadas** para uso operacional
- [ ] Premissas **aprovadas com ajustes** (listar abaixo)
- [ ] Premissas **reprovadas** — modelo precisa ser refeito

### Ajustes obrigatórios antes de usar

1. ________________________________________________
2. ________________________________________________
3. ________________________________________________

### Observações livres

_______________________________________________________________

_______________________________________________________________

_______________________________________________________________

---

## 11. Como testar no painel

1. Abrir https://tyre-eco.web.app/sag_ambiental.html  
2. Em **Premissas**, preencher custos diretos, Aluguel, Outros e % de rateio  
3. Ajustar rendimento da Secundária para o % real (soma 100%)  
4. Em **Lançamentos**, colocar as toneladas do período  
5. Em **Painel Geral**, conferir fluxo, rateio e margem  

Dúvidas de regra de cálculo: devolver este arquivo marcado na seção correspondente (R / E / Y / C / I / K / X / L).
