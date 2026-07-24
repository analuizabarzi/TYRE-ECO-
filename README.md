# 🏭 Tyre Eco — Sistema Logístico

Sistema web de gestão logística e comercial para a **Tyre Eco**, empresa de reciclagem de pneus baseada em Osasco/SP.

Coleta sucata automotiva (pneus, discos, filtros etc.) das redes **Campneus** e **DPaschoal** em todo o Brasil.

---

## 📁 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `sistema_tyre_eco.html` | Sistema principal com login e todos os módulos integrados |
| `vendas_v2.html` | Módulo de vendas refatorado (separado para desenvolvimento) |
| `vendas_melhorias.html` | Mix WhatsApp, recibo PDF, histórico, fiado, relatório |
| `consignacao.html` | Módulo de consignação com devolução e crédito |

> Todos os arquivos são **HTML standalone** — abrem direto no navegador, sem servidor, sem dependências instaladas.

---

## 🔐 Acesso ao sistema principal

**URL:** abrir `sistema_tyre_eco.html` no navegador

| Usuário | Senha | Perfil |
|---|---|---|
| `gestor` | `tyre2024` | Logística — roteizador, frota, financeiro, alertas |
| `motorista` | `tyre2024` | Herlon Carrera — rota do dia, check-in |
| `conferente` | `tyre2024` | Conferência operacional de descarga |
| `fiscal` | `tyre2024` | Conferência fiscal com IA — NF-e |
| `triagem` | `tyre2024` | Triagem de pneus por categoria e aro |
| `vendas` | `tyre2024` | Módulo comercial |

---

## 🗺️ Módulos implementados

### 👔 Gestor
- **Roteizador multi-rota** — K-Means geográfico, Nearest Neighbor TSP, geocodificação ViaCEP + Nominatim, Google Maps rota circular
- Seleção em lote por cidade, urgência (vencimento), filtro por UF
- Atribuição de motorista/veículo por rota
- Cálculo de km ida + volta e custo logístico estimado
- **Frota** — 33 veículos, 33 funcionários
- **Financeiro** — fechamento de rotas, custo logístico vs receita
- **Dashboard** — visão geral do dia
- **Alertas WhatsApp (Z-API)** — 2 alertas automáticos (ver seção abaixo)

### 🚛 Motorista
- Rota do dia com linha do tempo Base → Lojas → Base
- **Check-in em 4 etapas:** chegada → fotos (5 tipos) → 13 itens com quantidade → finalização (NF, assinatura digital canvas)
- Histórico de viagens

### 📋 Conferente Operacional
- Lista caminhões aguardando conferência
- Conferência nota por nota: lançamento do motorista vs conferido
- Divergências em destaque, atalho "Tudo igual"

### 🤖 Conferente Fiscal (IA)
- **NF Entrada** — upload XML NF-e, identifica loja pelo CNPJ, cruza com check-in
- **NF Saída** — converte pneus UN → TON, compara com NF emitida
- Parser NF-e namespace `http://www.portalfiscal.inf.br/nfe`

### 🔍 Triagem
- Só caminhões com conferência operacional concluída
- Grade 5 categorias × 8 aros: Carcaça, Risco, Meia Vida, Cortados, Lixo / 13,14,15,16,17,SUV,Camionete,Caminhão
- Totais em tempo real, botão confirmar só ativa quando soma = total conferido
- Dispara alerta WhatsApp se % Lixo ≥ limite

### 🛒 Vendas (`vendas_v2.html`)
- 4 abas: **Vendas · Devoluções · Extrato · Mix**
- Grade automática pelo cadastro do cliente (por medida para clientes tipo TCP, por aro para os demais)
- Crédito disponível do cliente aparece na venda e pode ser aplicado com 1 toque
- **Devoluções** — lança por aro/medida, gera crédito automaticamente
- **Extrato do cliente** — vendas, devoluções, créditos aplicados, pagamentos recebidos, saldo atual
- **Mix global** — por período + por cliente + por categoria (barras visuais)
- Envio de mix por WhatsApp ao confirmar venda

---

## 💬 Alertas WhatsApp (Z-API)

Dois alertas automáticos enviados para o **mesmo grupo** com mensagens diferentes:

| Alerta | Gatilho | Fonte |
|---|---|---|
| 🚚 Estourados | Check-in com estourados ≥ limite (padrão 30%) | Módulo motorista |
| 🔴 Lixo | Triagem finalizada com categoria Lixo ≥ limite (padrão 30%) | Módulo triagem |

**Configuração (perfil Gestor → Alertas WhatsApp):**
- Instance ID, Instance Token, Client Token (painel z-api.io)
- ID do grupo WhatsApp de destino
- Limite percentual configurável por alerta (slider)
- Mensagens customizáveis com variáveis dinâmicas
- Botões de simulação para testar sem esperar evento real
- Log de todos os envios com status e timestamp

---

## 🏗️ Arquitetura técnica

### Stack
- **Frontend:** HTML + CSS + JavaScript vanilla (sem framework)
- **Persistência:** `window.storage` (storage do claude.ai) — substituir por `localStorage` ao rodar fora do claude.ai
- **PDF:** jsPDF via CDN (gerado no browser)
- **Mapas:** Google Maps URL (rota circular, sem API key)
- **Geocodificação:** ViaCEP + Nominatim (rate limit 320ms entre requests)
- **Algoritmos:** K-Means++ geográfico (25 iterações) + Nearest Neighbor TSP
- **WhatsApp:** Z-API endpoint `send-text`
- **NF-e:** Parser XML nativo, namespace `http://www.portalfiscal.inf.br/nfe`

### Dados reais importados
- **33 funcionários** (PDF de relação de funcionários)
- **33 veículos**
- **699 clientes** (PDF histórico de vendas 2020-2026)
- **Tabela TCP Ecology Tyre** — 34 medidas × 5 aros com preços por medida
- **Tabelas Campneus e DPaschoal** — preços por item coletado
- **6 NF-e reais** processadas para testes do conferente fiscal

### Perfis de usuário
Todos compartilham a senha `tyre2024`. Cada perfil acessa apenas seus módulos relevantes.

---

## 📐 Decisões de arquitetura

| Decisão | Motivo |
|---|---|
| HTML standalone sem framework | Funciona offline, sem deploy, abre direto no celular |
| `window.storage` para persistência | API do claude.ai — trocar por `localStorage` em produção |
| Eventos via `addEventListener` (não `onclick` inline) | `onclick` inline quebra em alguns contextos do widget |
| Saudação pré-calculada antes do template literal | Aspas simples dentro de backtick quebram o JS parser |
| Geocodificação com delay de 320ms | Rate limit do Nominatim (1 req/seg) |
| K-Means com fallback de coordenadas por cidade | Quando ViaCEP ou Nominatim falham |

### Bug recorrente crítico ⚠️
**Aspas simples dentro de template literals quebram o parser.**

```js
// ❌ ERRADO — quebra
`${hora<12?'Bom dia':'Boa tarde'}`

// ✅ CORRETO — pré-calcular
const saudacao = hora<12?'Bom dia':'Boa tarde';
`${saudacao}`
```

---

## 🔌 Integrações externas

| Serviço | Uso | Status |
|---|---|---|
| **Z-API** | WhatsApp Business API | Configurar credenciais reais |
| **ViaCEP** | Geocodificação de CEPs | Funcional |
| **Nominatim** | Lat/lng a partir de endereço | Funcional |
| **Google Maps** | Rota circular para motoristas | Funcional (URL, sem API key) |
| **jsPDF** | Geração de recibo PDF no browser | Funcional |
| **Focus NFe / eNotas** | Emissão de NF-e real | Pendente — requer certificado A1/A3 |

---

## 📦 Preços por categoria (tabela padrão)

| Categoria | Aro 13 | Aro 14 | Aro 15 | Aro 16 | Aro 17 | SUV |
|---|---|---|---|---|---|---|
| Carcaça | R$35 | R$30 | R$25 | R$10 | R$5 | R$20 |
| Risco | R$35 | R$35 | R$35 | R$35 | R$35 | R$35 |
| Meia Vida | R$55 | R$55 | R$55 | R$55 | R$55 | R$55 |
| Cortados | R$45 | R$45 | R$45 | R$45 | R$45 | R$45 |
| Lixo | R$1 | R$1 | R$1 | R$1 | R$1 | R$1 |

Clientes com tabela individual (ex: TCP) têm preços por medida específica.

---

## 🗺️ Próximos passos

### Alta prioridade
- [ ] Integrar `vendas_v2.html` no `sistema_tyre_eco.html` (módulo vendas/perfil vendas)
- [ ] Substituir `window.storage` por `localStorage` para rodar fora do claude.ai
- [ ] Configurar Z-API com credenciais reais e testar alertas
- [ ] Testar roteizador com geocodificação real (ViaCEP + Nominatim)

### Média prioridade
- [ ] Estoque em tempo real (triagem alimenta → vendas consomem)
- [ ] Odômetro no check-in (km real para fechar custo logístico real)
- [ ] Importação automática de XML NF-e via e-mail
- [ ] Alerta de mix de venda abaixo de X% por aro
- [ ] DRE simplificado + fluxo de caixa

### Futuros
- [ ] Portal do cliente para declaração de devolução (Render.com + Supabase)
- [ ] Integração NF-e real via Focus NFe ou eNotas (certificado digital A1/A3)
- [ ] App mobile nativo (React Native) a partir dos módulos HTML validados

---

## 📞 Contexto do negócio

- **Empresa:** Tyre Eco — Osasco/SP (CEP 06233-040)
- **Operação:** coleta de sucata automotiva em lojas Campneus e DPaschoal
- **Cobertura:** 16 UFs, ~250 fornecedores ativos
- **Volume:** ~700 pneus por caminhão, múltiplas rotas simultâneas
- **Clientes de venda:** 699 cadastrados (borracharias, distribuidoras de pneus)

### Pesos médios por pneu (conferência NF saída)
- Pneu passeio: 6,5 kg
- Pneu estourado/inservível: 3,0 kg

### Itens coletados nas lojas
Pneus passeio, pneus estourados, amortecedor, bandeja, disco, filtro óleo, frascos óleo, mola, papelão, pastilha, plásticos, roda, sucata ferrosa

---

*Desenvolvido com Claude (Anthropic) — Junho 2026*
