# Desafio Técnico - Validação de Resumos de Acórdãos (Gen AI)

## Objetivo

Desenvolva uma solução baseada em modelos open-source (como LLaMA, Mistral, etc.) para analisar se as reivindicações feitas em um resumo de um acórdão do TCU (Tribunal de Contas da União) são verdadeiras com base no conteúdo do documento original.
A cada parágrafo do resumo, sua tarefa é avaliar a veracidade das afirmações, fornecendo justificativas.
Insumos

* 2 documentos completos de acórdãos do TCU em .txt ou .pdf.
* 3 resumos correspondentes, contendo uma série de afirmações de diferentes naturezas.

Os resumos não têm estrutura fixa e podem conter qualquer tipo de afirmação (tributária, contratual, processual etc.).

## Resultado

o a gente Identificou 24 reividica;óes aonde , definiu 19 como incorretas e 5 como corretas

Foi utilizado o modelo **[`mistralai/Mistral-7B-Instruct-v0.3`]()** para atuar como um  **analista jurídico automatizado** , capaz de identificar e avaliar reivindicações em resumos de processos.

#### Estratégias Utilizadas

* FAISS (Facebook AI Similarity Search): empregado para indexação e busca vetorial, facilitando a recuperação de contextos relevantes e tornando as análises mais rápidas e escaláveis.(vi em aula e achei interessante empregar aqui)
* Few-Shot: prompts foram estruturados com exemplos, aumentando a precisão do modelo na classificação das reivindicações(no primeiro momento ele usou as revidicações como evidencia).
* Extração e Análise: dividido em etapas (detecção de reivindicações → avaliação com contexto → output).

#### Funções Criadas

extrair_reivindicacoes(texto_resumo)

Responsável por identificar automaticamente reivindicações em um resumo jurídico em txt.

analisar_reivindicacao_com_contexto(reivindicacao, contexto)

Avalia se uma reivindicação no resumo txt  é suportada ou não pelo contexto fornecido em pdf, retornando rótulos como Correta ou Incorreta.

Funções auxiliares

Criadas para formatar os prompts, tratar os resultados do modelo e integrar com o FAISS, garantindo que as respostas estejam em formato JSON de acordo com desafio.
