# Desafio Técnico - Validação de Resumos de Acórdãos (Gen AI)

## Objetivo
Desenvolva uma solução baseada em modelos open-source (como LLaMA, Mistral, etc.) para analisar se as reivindicações feitas em um resumo de um acórdão do TCU (Tribunal de Contas da União) são verdadeiras com base no conteúdo do documento original.
A cada parágrafo do resumo, sua tarefa é avaliar a veracidade das afirmações, fornecendo justificativas.
Insumos

* 2 documentos completos de acórdãos do TCU em .txt ou .pdf.
* 3 resumos correspondentes, contendo uma série de afirmações de diferentes naturezas.

Os resumos não têm estrutura fixa e podem conter qualquer tipo de afirmação (tributária, contratual, processual etc.).

## Entrega esperada
Um repositório GitHub contendo:
1. Um notebook (.ipynb) ou script Python que:
* Lê um documento original e seu respectivo resumo;
* Identifica as reivindicações no resumo;
* Avalia cada reivindicação como:
    1. Correta
    2. Incorreta, com justificativa baseada no trecho correspondente
* Utiliza modelo open-source (ex: LLaMA 2 7B, Mistral, Phi-2 etc.);
2.	Um único JSON com análise de cada reivindicação para cada resumo:

```json
[
    {
        "doc_name": "Acórdão 733 de 2025 Plenário",
        "claim_text": "O banco...",
        "label": "Correta",
        "evidence": "Reinvidicação correta, pois...",
        "summary_id": 1,
        "claim_id": 0 // Id sequencial, incremental, iniciando em 0
    },
    {
        "doc_name": "Acórdão 733 de 2025 Plenário",
        "claim_text": "O agente...",
        "label": "Incorreta",
        "evidence": "Justificativa...",
        "summary_id": 1,
        "claim_id": 1
    }
]
```

## Requisitos técnicos
* Utilizar apenas modelos e bibliotecas de código aberto (pode ser HuggingFace, GGUF + llama.cpp, etc.).
* O código deve rodar localmente (CPU ou GPU), contudo, podendo utilizar provedores externos para consumir LLMs.

## Análises e limitações

Providencie uma análise quantitativa e qualitativa do método proposto.
Identifique e apresente as métricas escolhidas.

## Critério de avaliação

Serão priorizados: (i) robustez da avaliação (correta/incorreta), (ii) clareza do código, (iii) eficiência de tokens.

## Objetivo extra

Resolver o desafio com o menor número de tokens (entrada + saída) possível.

## Dica

A frase "O TCU anulou o contrato e aplicou multa de R$ 500 mil ao consórcio" possui <b>duas</b> reivindicações.