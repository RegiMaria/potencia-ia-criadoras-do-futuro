# Prompt · Análise de rótulo de ração · v1

| | |
|---|---|
| **Framework** | PACEF |
| **Ferramenta** | ChatGPT (versão gratuita) |
| **Entrada** | Foto da lista de ingredientes + texto |
| **Módulo** | [04 · Olhando para seu contexto](../resumos/bloco-1/04-olhando-para-seu-contexto.md) |
| **Projeto** | Candidato na [matriz de viabilidade](../projeto/01-matriz-de-viabilidade.md) |

## Objetivo

Entender, em linguagem simples, o que tem na ração dos meus cachorros: ingredientes sintéticos (conservantes, corantes, aromatizantes) e possíveis transgênicos.

## Montando o prompt com o PACEF

| Letra | Meu prompt |
|---|---|
| **P** · Papel | Atue como especialista em nutrição de cães e em leitura de rótulos de ração. |
| **A** · Ação | Analise a lista de ingredientes da foto que vou enviar e identifique ingredientes sintéticos (conservantes, corantes, aromatizantes) e possíveis transgênicos. |
| **C** · Contexto | Tenho cachorros e compro ração premium. Não sou especialista e quero entender, em linguagem simples, o que estou oferecendo a eles. |
| **E** · Exemplo | Exemplo do que espero: "BHA: conservante sintético, usado para evitar que a gordura estrague." |
| **F** · Formato | Tabela com as colunas: ingrediente, tipo (natural, sintético ou possível transgênico), para que serve e ponto de atenção. No final, um resumo de três linhas. Se não for possível afirmar algo só pelo rótulo, diga isso. |

## Prompt enviado

Os rótulos do PACEF servem só para montar. Na hora de enviar, ficou assim:

```text
Atue como especialista em nutrição de cães e em leitura de rótulos de ração.

Analise a lista de ingredientes da foto que vou enviar e identifique ingredientes
sintéticos (conservantes, corantes, aromatizantes) e possíveis transgênicos.

Tenho cachorros e compro ração premium. Não sou especialista e quero entender,
em linguagem simples, o que estou oferecendo a eles.

Exemplo do que espero: "BHA: conservante sintético, usado para evitar que a
gordura estrague."

Apresente em uma tabela com as colunas: ingrediente, tipo (natural, sintético ou
possível transgênico), para que serve e ponto de atenção. No final, faça um resumo
de três linhas. Se não for possível afirmar algo só pelo rótulo, diga isso.
```

**Imagem enviada:**

<p align="center">
  <img
    width="400"
    alt="Lista de ingredientes da ração usada no teste"
    src="https://github.com/user-attachments/assets/8ad38352-32aa-4dfd-912f-b49d6def8bde"
  />
</p>

## Resultado

**Principais conclusões da IA:**
1. Não encontrou BHA, BHT nem corantes declarados. O antioxidante informado é concentrado de tocoferóis, ligado à vitamina E.
2. Vitaminas, minerais e aminoácidos adicionados são comuns para completar a nutrição. "Produzido industrialmente" não significa prejudicial.
3. O maior ponto de interrogação é o **realçador de palatabilidade**, que não tem a substância especificada, e a origem das matérias-primas vegetais.
4. Sobre transgênicos, nada pode ser afirmado pelo rótulo. A fibra de cana tem uma possibilidade teórica, porque existem variedades de cana transgênica aprovadas no Brasil, mas não há evidência.
5. Frango alimentado com ração transgênica não é frango transgênico.

<details>
<summary><b>Ver a tabela gerada (resumida)</b></summary>

| Ingrediente | Tipo | Para que serve | Ponto de atenção |
|---|---|---|---|
| Concentrado de tocoferóis | Natural (provável) | Antioxidante, protege as gorduras | Rótulo não informa a origem exata |
| Ácido propiônico | Aditivo, origem indeterminada | Conservante contra fungos | Não dá para saber se é de fermentação ou síntese |
| Realçador de palatabilidade | Aditivo sensorial, origem não informada | Deixa a ração mais saborosa | Substância não especificada, ponto a investigar |
| Minerais (cloretos, sulfatos, iodato, selenito) | Compostos minerais | Fontes de sódio, potássio, ferro, cobre, zinco, iodo, selênio | Nutrientes, não conservantes |
| Vitaminas (A, D3, E, K3, complexo B, C) | Adicionadas, várias industriais | Completar a nutrição | Rótulo não diz quais são sintéticas |
| Lisina, metionina, taurina | Aminoácidos adicionados | Proteínas e metabolismo | Processo de produção não informado |
| Fécula de mandioca, farinha de ervilha, fécula de batata | Vegetal | Carboidrato e estrutura | Não dá para afirmar se são transgênicos |
| Fibra de cana-de-açúcar | Vegetal | Fibra | Possibilidade teórica de origem transgênica, sem evidência |
| Frutas e vegetais desidratados | Vegetal | Fibras e palatabilidade | Categoria genérica, sem detalhes |
| Biomassa de microalgas | Biológica | Fonte de ômega-3 (DHA) | Linhagem não informada |
| Parede celular de levedura | Biológica | Saúde intestinal | Linhagem não informada |
| Frango, vísceras, fígado | Animal | Proteína e gordura | Não são transgênicos por si |

</details>

## Avaliação

**✅ O que funcionou**
- A tabela veio no formato que pedi, com as quatro colunas.
- A instrução "se não for possível afirmar, diga isso" funcionou. A IA disse várias vezes que o rótulo não permitia concluir se um ingrediente era transgênico, em vez de inventar.
- O exemplo do BHA orientou a busca: ela procurou BHA, BHT e corantes e disse claramente que não encontrou.

**❌ O que não funcionou**
- Pedi um resumo de três linhas e ela escreveu várias seções a mais.
- Ela citou órgãos como MAPA, AAFCO e CTNBio. Numa solução real, eu precisaria conferir essas fontes.

**💡 O que aprendi**
- A última frase do formato faz diferença. Pelo rótulo nem sempre dá para saber se um ingrediente é transgênico, e pedir para a IA admitir quando não sabe reduz o risco de ela inventar uma resposta.
- A parte mais útil foi saber o que o rótulo **não** informa. Isso me fez repensar o problema: talvez não seja só falta de entendimento, mas falta de transparência nos rótulos.
- O teste levou minutos, com ferramenta gratuita. Bom sinal para acesso e tempo de teste na matriz.

## Ideias para a v2

- Deixar o limite de tamanho mais firme: "resumo de no máximo três linhas, sem seções extras depois dele".
- Pedir uma seção própria para **"o que o rótulo não informa"**, já que foi a parte mais útil.
- Colocar dados reais dos meus cães no contexto (quantidade, porte, idade).
- Testar o mesmo prompt em outra LLM (Claude ou Gemini) e comparar, como no módulo 05.
