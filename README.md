# 🏭 Tyre Eco — Sistema Logístico

Sistema web de gestão logística, financeira e comercial da **Tyre Eco**, empresa de reciclagem de pneus baseada em Osasco/SP.

Coleta sucata automotiva (pneus, discos, filtros, etc.) das redes **Campneus**, **DPaschoal** e outras, em todo o Brasil, e revende os materiais recicláveis a clientes cadastrados.

---

## 📁 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | **Sistema completo** — login, todos os módulos, todo o negócio. Este é o único arquivo em produção. |
| `firebase.json` / `.firebaserc` | Configuração do Firebase Hosting |
| `.github/workflows/deploy.yml` | Deploy automático (ver seção "Publicação") |

> Arquivos antigos como `sistema_tyre_eco.html`, `vendas_v2.html`, `vendas_melhorias.html`, `consignacao.html`, `cadastros (12).html`, `tyre_eco (1).html` são **protótipos anteriores**, já incorporados ao `index.html`. Podem ser apagados do repositório sem perda de funcionalidade.

O sistema é uma aplicação **standalone** (HTML + CSS + JS num único arquivo) — não tem build, não tem `npm install`, não tem servidor próprio. O banco de dados é o **Firebase Firestore**, então é preciso estar online.

---

## 🔐 Acesso ao sistema

Cada colaborador tem **login individual** (usuário + senha), criado pelo Gestor na tela **Usuários**. Não existe mais senha compartilhada.

Cada usuário tem um **perfil** (Gestor, Motorista, Conferente Operacional, Conferente Fiscal, Triagem, Vendas, Financeiro, Emissão de NF, Logística) que define um conjunto padrão de módulos visíveis — mas o Gestor pode **customizar exatamente quais módulos cada pessoa vê**, módulo por módulo, independente do perfil (tela Usuários → botão 🔑 Permissões).

A trava de permissão é aplicada tanto na tela (esconde os cards) quanto na abertura do módulo (`abrirModulo`), então não dá pra contornar digitando o módulo direto no console do navegador.

---

## 🗺️ Módulos

### 👔 Gestor
- **Roteirizador** — seleção de lojas por cidade/UF/urgência, geocodificação (ViaCEP + Nominatim), K-Means + Nearest Neighbor, atribuição de motorista/veículo/ajudante/frete, link de rota no Google Maps, histórico de rotas criadas
- **Cadastros** (abas): Pessoas · Fornecedores · Itens · Veículos · Clientes · Medidas · Custos por rede
- **Financeiro** — fechamento de rotas, Plano de Contas, Contas a pagar e a receber (CRUD completo, parcelamento, registro de pagamento parcial)
- **Relatórios** — consolidado, contas a pagar, contas a receber, pagos/recebidos, vendas, com filtros de período
- **Emitir NF** — gera a ficha de dados da NFS-e (preenchimento manual na prefeitura; não emite a nota oficialmente)
- **Importar dados** — importação por Excel/CSV de vendas, contas e fornecedores, com detecção automática de colunas, checagem de duplicados e histórico de importações
- **Alertas WhatsApp (Z-API)** — três alertas configuráveis (ver seção própria)
- **Usuários** — criação de login por colaborador + permissões granulares por módulo
- **Dashboard** — visão geral do dia

### 🧭 Logística
- Mesmo Roteirizador do Gestor
- **Painel de Motoristas** — acompanha a viagem em andamento (progresso de check-ins, próxima parada) e lista as rotas já criadas

### 🚛 Motorista
- Rota do dia atribuída
- **Check-in de coleta** por loja: itens coletados (13 tipos), assinatura digital, NF/observações
- Ao confirmar o check-in, o sistema já **gera automaticamente uma conta a pagar** para a rede daquela loja, calculada pelos itens coletados × tabela de custo vigente (ver Cadastros → Custos por rede)
- Histórico de viagens

### 📋 Conferente Operacional
- Lista caminhões aguardando conferência
- Confere nota por nota: lançamento do motorista vs. conferido, divergências em destaque

### 🧾 Conferente Fiscal
- **NF Entrada** — cruza XML de NF-e das lojas com o check-in do motorista
- **NF Saída** — compara pneus (UN → TON) com a NF emitida na venda do material

### 🔍 Triagem
- Grade por categoria (Carcaça, Risco, Meia Vida, Cortados, Lixo) × aro
- Dispara alerta de WhatsApp se % de Lixo passar do limite configurado

### 🛒 Vendas
- Grade de preços por cliente (por aro ou por medida específica, conforme cadastro)
- **Foto do produto** antes de finalizar a venda (comprimida automaticamente, guardada por venda)
- **Regra de mix de venda** configurável: alerta (não bloqueia) quando Aro 13 ou Aro 14 passam do % combinado do mix total — limites ajustáveis em Alertas
- Resumo do mix sempre exibido ao final da venda
- **Imprimir pedido de venda** (cliente, itens, pagamento, foto)
- **Gerar ficha de NF** direto da venda confirmada, já preenchida com CNPJ/endereço/e-mail do cliente (se cadastrados)
- Histórico de vendas, edição e exclusão de vendas já lançadas

---

## 🧩 Cadastros

| Aba | Conteúdo |
|---|---|
| **Pessoas** | Funcionários e ajudantes |
| **Fornecedores** | Lojas de coleta — Rede, Loja, Cód. loja, Endereço completo, Cidade/UF/CEP, Periodicidade de coleta, Observações. Suporta importação em massa por Excel/CSV. |
| **Itens** | Volume (m³) por item coletado |
| **Veículos** | Frota e capacidade do baú |
| **Clientes** | Clientes de venda — nome, categoria/tabela de preço (por aro ou por medida), e dados fiscais (CNPJ, endereço, e-mail) usados para preencher a NF automaticamente |
| **Medidas** | Catálogo de medidas de pneu por aro, usado nas tabelas de preço detalhadas |
| **Custos por rede** | Custo de cada item coletado, por rede (Campneus, DPaschoal, etc.), com **vigência de contrato** (início/fim). Alimenta a geração automática de contas a pagar. |

---

## 💰 Financeiro

- **Plano de Contas** — categorias de receita e despesa configuráveis
- **Contas a pagar** — manuais (fornecedores, frota, salários, etc.) ou **geradas automaticamente pela coleta** (marcadas com a rede e a loja de origem); suporta parcelamento e registro de pagamento parcial
- **Contas a receber** — clientes, com o mesmo suporte a parcelamento/pagamento parcial
- Se uma coleta for feita numa loja de rede sem tabela de custo configurada, a conta ainda é gerada (valor R$ 0) e fica sinalizada, para não perder o rastro

---

## 💬 Alertas WhatsApp (Z-API)

Três alertas configuráveis, todos enviados para o mesmo grupo:

| Alerta | Gatilho |
|---|---|
| 🚚 Estourados | Check-in com % de pneus estourados ≥ limite (slider, padrão 30%) |
| 🔴 Lixo | Triagem finalizada com % de Lixo ≥ limite (slider, padrão 30%) |
| 📊 Mix de venda | Não envia WhatsApp — controla os limites de Aro 13/14 usados no alerta visual da tela de Vendas |

Configuração em **Alertas WhatsApp** (perfil Gestor): credenciais Z-API, ID do grupo, limites, mensagens customizáveis com variáveis, simulação de disparo, log de envios.

---

## 🚀 Publicação (deploy)

O sistema roda em dois endereços, sincronizados automaticamente:

- **GitHub Pages:** `https://analuizabarzi.github.io/TYRE-ECO-/`
- **Firebase Hosting:** `https://tyre-eco.web.app`

Fluxo: qualquer commit de `index.html` na branch `main` já atualiza o GitHub Pages; o GitHub Actions (`.github/workflows/deploy.yml`) dispara em seguida um deploy automático no Firebase Hosting, usando a credencial guardada no secret `FIREBASE_SERVICE_ACCOUNT` do repositório. Não é preciso terminal nem `firebase deploy` manual.

Pra atualizar o sistema: baixe o `index.html`, edite, e suba de novo pelo **Add file → Upload files** do GitHub — os dois sites atualizam sozinhos em menos de um minuto.

---

## 🔥 Firebase

- **Projeto:** `tyre-eco` (região `southamerica-east1`)
- **Autenticação:** Firebase Auth (e-mail/senha; login de usuário vira `usuario@tyreeco.app` internamente)
- **Banco de dados:** Firestore
  - `usuarios/{uid}` — perfil, permissões, dados de login
  - `app_storage/{chave}` — armazena a maior parte dos dados do sistema (cadastros, vendas, contas, custos, etc.) através de um shim (`window.storage`) que expõe `get/set` como se fosse local, mas grava no Firestore
  - `venda_foto_{id}` — foto de cada venda, guardada separadamente do histórico principal (evita estourar o limite de tamanho de documento)

⚠️ Fotos e arquivos grandes **nunca** devem ser guardados dentro de arrays grandes salvos como um único documento (histórico de vendas, contas, etc.) — isso já causou risco de estourar o limite de 1 MB por documento do Firestore no passado. Sempre usar uma chave própria por registro quando o conteúdo for pesado (base64 de imagem, por exemplo).

---

## ⚠️ Limitações conhecidas

- O acompanhamento de "viagem em andamento" (Painel de Motoristas) hoje segue **uma viagem ativa por vez**, não múltiplos motoristas rodando simultaneamente com estado independente. Se isso virar necessário no dia a dia, é preciso um trabalho maior para dar identidade própria a cada rota/motorista em andamento.
- A emissão de NF é uma **ficha auxiliar**, não uma integração real com a prefeitura — o lançamento final ainda é manual no portal da NFS-e.

---

## 🛠️ Convenções técnicas (para quem for mexer no código)

- Eventos via `addEventListener`, nunca `onclick` inline.
- Toda saída de texto que vem do usuário (nome, observação, endereço) passa por `escapeHtml()` antes de entrar no HTML.
- Confirmações e avisos usam `confirmarAcao()` / `mostrarToast()` / `abrirModal()` — não usar `confirm()`/`alert()`/`prompt()` nativos do navegador em telas novas.
- Arrays de cadastro (`FORNS_ROT`, `CLIENTES_VND`, etc.) são declarados com `const` — para remover itens, usar `.splice()`, nunca reatribuir (`arr = arr.filter(...)` quebra, pois é `const`).
- Ao adicionar um novo tipo de dado importável por Excel, seguir o padrão em `CAMPOS_IMPORT` / `IMPORT_ALIASES` / `processarLinhasImport` / `_renderImportPreview`.

---

## 📞 Contexto do negócio

- **Empresa:** Tyre Eco — Osasco/SP
- **Operação:** coleta de sucata automotiva em lojas Campneus, DPaschoal e outras redes
- **Itens coletados:** pneus passeio, pneus estourados, amortecedor, bandeja, disco, filtro óleo, frascos óleo, mola, papelão, pastilha, plásticos, roda, sucata ferrosa

---

*Desenvolvido com Claude (Anthropic), com contribuições de Ana Luiza Barzi e equipe.*
