# 📡 Prospecção por Sinais

[![Prospecção por Sinais](guia/assets/banner.jpg)](https://inematds.github.io/prospeccao-por-sinais/guia/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

## O que é

Este é um kit gratuito para quem vende para empresas e quer prospectar sem disparar e-mail para lista fria. A ideia é procurar **sinais**, ou seja, acontecimentos públicos que mostram que uma empresa pode precisar de você agora (uma vaga aberta, um produto lançado, um diretor novo), e só então achar a pessoa que decide e escrever uma mensagem que cita esse sinal. O Claude Code faz o trabalho pesado usando o Clay (uma plataforma de dados de empresas e contatos) e entrega uma planilha para você revisar. Você precisa do Claude Code, de uma conta no Clay (tem plano grátis e teste) e de uma tarde para preencher o contexto do seu negócio.

## 📖 Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/prospeccao-por-sinais/guia/**

## O processo, do início ao fim

Quem faz: 🧠 você no Claude Code · ⚙️ Clay/script · 🤖 agente (Claude Code trabalhando sozinho)

| # | Passo | Comando | Quem |
|---|-------|---------|------|
| 1 | Baixar o kit e abrir o Claude Code na pasta | `git clone https://github.com/inematds/prospeccao-por-sinais.git` · `cp -r prospeccao-por-sinais/kit ~/minha-prospeccao` · `cd ~/minha-prospeccao && claude` | 🧠 |
| 2 | Instalar o plugin do Clay (Claude Code ≥ 2.1.91) | `/plugin marketplace add clay-run/agent-plugins` · `/plugin install clay@clay-plugins` · "Rode a skill clay:setup" | 🧠 |
| 3 | Preencher o contexto do negócio | editar `contexto/*.md` (modelo em `contexto/exemplo/`) | 🧠 |
| 4 | Definir os sinais | editar `sinais.yaml` · opcional: `npx skills add clay-run/clay-skill-creator --skill customer-signal-generator` | 🧠 + 🤖 |
| 5 | ICP: lista de empresas (10 linhas primeiro) | Passo 1 de `prompts/passo-a-passo.md` | 🤖 + ⚙️ |
| 6 | Sinal de contratação monitorado | Passo 2 | 🤖 + ⚙️ |
| 7 | Agente de pesquisa (lançamento de produto) | Passo 3 | 🤖 + ⚙️ |
| 8 | Decisor só onde há sinal (condição de execução) | Passo 4 | 🤖 + ⚙️ |
| 9 | E-mail em cascata + verificação | Passo 5 | ⚙️ |
| 10 | Mensagem com contexto (assunto + corpo citando o sinal) | Passo 6 — ou tudo de uma vez com `/goal` (`prompts/goal-prospeccao.md`) | 🤖 |
| 11 | CSV final para revisão | `saida/leads-AAAA-MM-DD.csv` (colunas em `colunas-csv.md`) | 🤖 |
| 12 | Revisão humana | ler as linhas com `revisar = sim`, corrigir | 🧠 |
| 13 | Importar no sequenciador e enviar devagar | importar CSV → campanha; domínio secundário aquecido, poucos envios/dia, spam < 0,3% | 🧠 + ⚙️ |
| 14 | Supressão | quem pediu para sair vai para `supressao.csv` no mesmo dia | 🧠 |

Regra de ouro (está no `kit/CLAUDE.md`): o agente **nunca gasta crédito sem pedir**, **roda 10 linhas antes** e **nunca envia nada**.

## O kit

```
kit/
├── CLAUDE.md                 regras do agente (crédito, 10 linhas, revisão, opt-out, LGPD)
├── contexto/                 6 modelos: perfil-do-negocio, oferta, casos, provas, faq, tom-de-voz
│   └── exemplo/              os mesmos 6, preenchidos com uma empresa FICTÍCIA
├── prompts/
│   ├── goal-prospeccao.md    prompt para /goal com linha de chegada verificável
│   └── passo-a-passo.md      um prompt por passo do fluxo
├── sinais.yaml               sinais de exemplo com janela de validade e peso
├── colunas-csv.md            colunas da planilha de saída
├── checklist-lgpd.md         checklist prático (não é parecer jurídico)
└── supressao.csv             quem pediu para sair
```

## Custos (documentação pública do Clay, conferido em 01/11/2026)

- Grátis: 100 créditos/mês. Teste de 14 dias: 1.000 créditos. Plano Launch: a partir de US$ 185/mês (2.500 créditos + 15.000 ações).
- Na cascata, os fornecedores padrão de e-mail e celular devolvem o crédito quando não acham; celular não está disponível no grátis nem no teste.
- Fonte: https://github.com/clay-run/public-docs

## Referências

- Plugin do Clay para agentes: https://github.com/clay-run/agent-plugins
- Gmail — diretrizes para remetentes: https://support.google.com/a/answer/81126?hl=pt-BR
- LGPD (Lei 13.709/2018): https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm · ANPD: https://www.gov.br/anpd

---

Conteúdo aberto e gratuito do [INEMA.CLUB](https://inema.club).
