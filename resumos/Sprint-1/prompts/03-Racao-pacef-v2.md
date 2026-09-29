# Prompt - Análise de rótulo de ração - v2

| | |
|---|---|
| **Framework** | PACEF |
| **Ferramenta** | Gemini |
| **Entrada** | A mesma foto e o mesmo prompt da [v1](racao-pacef-v1.md) |
| **Módulo** | [05 · Como transformar um problema em pergunta](../resumos/bloco-1/05-problema-em-pergunta.md) |

## O que mudou em relação à v1

**Só a ferramenta.** O prompt e a imagem são idênticos aos da [v1](racao-pacef-v1.md), feita no ChatGPT. O objetivo foi comparar duas LLMs, como pede o módulo 05.

## Resultado

**Principais conclusões do Gemini:**
1. Identificou a marca e a linha do produto _(omitidas aqui)_.
2. Destacou conservantes naturais (extratos de alecrim, chá verde e hortelã, e tocoferóis) no lugar de BHA e BHT.
3. Classificou o ácido propiônico como sintético, mas seguro.
4. Apontou o hidrolisado de fígado de aves e suíno como palatabilizante natural.
5. Disse que a fórmula tem baixíssimo risco de transgênicos por não usar milho nem soja.
6. Concluiu que é uma ração de excelente qualidade e uma opção segura.

<details>
<summary><b>Ver a tabela gerada (resumida)</b></summary>

| Ingrediente | Tipo | Para que serve | Ponto de atenção |
|---|---|---|---|
| Extratos de alecrim, chá verde, hortelã e tocoferóis | Natural | Conservantes e antioxidantes | Substituem BHA e BHT |
| Ácido propiônico | Sintético | Antifúngico | Considerado seguro e comum |
| Hidrolisado de fígado de aves e suíno | Processado, origem animal | Palatabilizante | Dá sabor sem aroma artificial |
| Premix de vitaminas e minerais | Sintético / idêntico ao natural | Suplementação | Vitamina K3 (menadiona) é sintética |
| Mandioca, batata, ervilha | Natural | Energia e estrutura | Sem milho nem soja |
| Fibra de cana e polpa de beterraba | Natural / possível transgênico (hipótese) | Fibras | Não dá para afirmar pelo rótulo |
| Corantes artificiais | Não contém | — | Cor vem dos ingredientes |

</details>

## Comparando com a v1 (ChatGPT)

| | ChatGPT | Gemini |
|---|---|---|
| Formato da tabela | ✅ Respeitou | ✅ Respeitou |
| Resumo de três linhas | ❌ Escreveu várias seções a mais | ✅ Quase: um parágrafo curto |
| Admitiu quando não sabia | ✅ Várias vezes | ⚠️ Em parte: foi cauteloso na fibra de cana, mas afirmou "livre de aromatizantes sintéticos" e "baixíssimo risco de transgênicos" |
| Tom | Informativo e neutro | Avaliativo: "excelente qualidade", "opção segura" |
| Identificou o produto | Não | Sim, marca e linha |
| Ingredientes citados | Realçador de palatabilidade sem especificação, microalgas, levedura | Extratos botânicos, hidrolisado de fígado, polpa de beterraba |

## Avaliação

**⚠️ A descoberta mais importante:** com a mesma foto, as duas IAs citaram ingredientes **diferentes**. O ChatGPT falou de um realçador de palatabilidade não especificado; o Gemini falou de hidrolisado de fígado. O ChatGPT não citou alecrim nem chá verde; o Gemini não citou microalgas nem levedura. Pelo menos uma delas leu errado, deixou algo de fora ou completou com informação que não está na foto.

🚧 **Conferência no rótulo:** _o que realmente aparece na lista de ingredientes?_

**💡 O que aprendi**
- Uma resposta bem escrita e confiante não é garantia de resposta certa. O Gemini soou mais seguro, e justamente por isso precisa ser conferido.
- O Gemini parece ter usado conhecimento sobre a marca, e não só o que estava na foto. Isso explica por que ele "sabia" mais, mas também aumenta o risco de misturar informação.
- Para uma ferramenta que ajuda a decidir o que um cachorro vai comer, cautela vale mais que confiança.

## Ideias para a v3

- Pedir primeiro: **"Transcreva a lista de ingredientes exatamente como está na foto, sem acrescentar nada"**. Só depois de eu conferir a lista, pedir a análise.
- Acrescentar: **"Use apenas as informações da imagem. Não use conhecimento sobre a marca ou o produto."**
- Pedir para não fazer avaliação geral ("excelente", "segura"), só explicar os ingredientes.
