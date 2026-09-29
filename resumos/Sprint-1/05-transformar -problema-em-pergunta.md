<p align="center">
  <img
    width="100"
    height="100"
    alt="Banner"
    src="https://github.com/user-attachments/assets/821167d0-128e-4da7-bec6-2035ceb97547" 
  />
</p>

# 05 · Como transformar um problema em pergunta para IA resolver

> Bloco 1 - Trilha Criadoras do Futuro com IA - 2026

## Objetivo
Traduzir um problema do cotidiano em um formato que a IA entenda e consiga resolver.

## Ideias principais

**O que a IA entende**: estrutura lógica, dados, padrões e linguagem.

**Entradas além de texto**: posso enviar arquivos, fotos e planilhas no prompt.

**Do problema à pergunta**
| Problema | Pergunta para a IA |
|---|---|
| Esqueço compromissos | Como a IA pode me ajudar a planejar e lembrar dos compromissos? |
| Cliente demora para responder | Que tipo de IA posso usar para automatizar o follow-up? |
| Levo horas para criar posts | Existe uma IA que me ajude a gerar ideias? |

**Prompt completo no início, perguntas simples depois**: com o contexto já dado na conversa, posso refinar com perguntas curtas.

**Comparar ferramentas**: o mesmo tipo de pedido no ChatGPT e no Claude gera respostas diferentes. Se eu não peço um formato, cada uma escolhe o seu.

## Prática
Pegar um problema real, reescrever como pergunta e testar em duas LLMs diferentes.

## Frase-chave
> A IA não resolve problemas mal contados.

## Minha reflexão

_Como ficaram os meus problemas escritos como pergunta?_

| Problema | Pergunta para a IA |
|---|---|
| Falta informação clara sobre a composição das rações | Como a IA pode ler o rótulo da ração e me explicar, em linguagem simples, quais ingredientes são sintéticos ou possivelmente transgênicos? |
| Falta um plano estruturado para meus estudos AWS | Como a IA pode dividir o conteúdo da certificação até a data da prova, com simulados e revisões, e me ajudar a acompanhar o progresso? |
| Não consigo comparar os preços das minhas compras mês a mês | Como a IA pode ler minhas notas fiscais e me mostrar quais produtos ficaram mais caros ou mais baratos em relação ao mês anterior? |
| Falta informação reunida sobre prestadores de serviços para pets | Como a IA pode me ajudar a comparar prestadores de serviços para pets perto de mim, considerando experiência e avaliações? |

Percebi que escrever como pergunta me obriga a dizer **o que** eu quero que a IA faça e **para quê**. O problema deixa de ser uma reclamação e vira um pedido.

### Comparando ferramentas

_Qual ferramenta respondeu melhor?_

Rodei o mesmo prompt da ração, com a mesma foto, no ChatGPT e no Gemini:

| | ChatGPT (gratuito) | Gemini |
|---|---|---|
| Respeitou o formato? | Sim, mas passou do resumo de três linhas | Sim, com resumo curto |
| Admitiu quando não sabia? | Sim, várias vezes | Em parte, fez algumas afirmações sem base no rótulo |
| Tom | Informativo e neutro | Avaliativo ("excelente", "segura") |
| Ingredientes citados | Diferentes dos do Gemini | Diferentes dos do ChatGPT |

**Qual respondeu melhor?** Depende do que eu valorizo. O Gemini foi
mais direto e agradável de ler. O ChatGPT foi mais cauteloso.
Mas a maior lição foi outra: com a mesma foto, as duas citaram ingredientes 
diferentes. Quem decide qual está certa sou eu, conferindo o rótulo.
É o senso crítico que o módulo 02 pedia, na prática.

Com a mesma foto, o ChatGPT citou um "realçador de palatabilidade" sem especificação,
microalgas e levedura. O Gemini citou extratos de alecrim, chá verde e hortelã,
hidrolisado de fígado e polpa de beterraba, e nenhum dos itens do ChatGPT.

Pelo menos uma delas leu errado, pulou parte da lista ou completou com informação de fora da foto.

Mais uma coisa: o Gemini identificou a marca e a linha do produto.
Isso sugere que ele usou o que já sabia sobre aquela ração,
e não só o que estava na imagem.
Por isso ele parece "saber mais" e soa mais confiante,
com frases como "opção segura" e "baixíssimo risco de transgênicos".
Só que essas afirmações vão além do que o rótulo permite concluir,
**justamente o que o meu prompt pedia para evitar.**

`racao-pacef-v2.md`: registro do teste no Gemini, com a comparação lado
a lado e as ideias para a v3. 

Deixei a marca de fora, seguindo o cuidado de não associar publicamente o produto às dúvidas da análise.

> ### Vale incluir um passo em que a IA primeiro transcreve a lista de ingredientes e eu confiro antes da análise.

➡️ Registros: [`racao-pacef-v1.md`](../../prompts/racao-pacef-v1.md) (ChatGPT) · [`racao-pacef-v2.md`](../../prompts/racao-pacef-v2.md) (Gemini)
