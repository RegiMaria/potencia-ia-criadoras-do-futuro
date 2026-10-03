# 02 · Prompt: Geração de Fluxo Visual no Whimsical (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 2 · Módulo 12: Desenhando o fluxo da sua solução**

---

## Contexto & Ferramenta
No **Módulo 12**, a professora apresenta ferramentas para a criação de mapas visuais, fluxogramas e organização de conhecimento:
* **Whimsical** *(Principal recomendada do curso para fluxos e mapas mentais)*: possui IA integrada para gerar diagramas de fluxo automáticos com caixas e conexões a partir de comandos em linguagem natural.
* **NotebookLM** *(Organização e estudo de documentos)*: ideal para centralizar bases de dados, PDFs e notas com privacidade e gerar resumos em áudio/mapas mentais.
* **Napkin AI** *(Módulo 11)*: alternativa ágil para geração de infográficos e diagramas de processos em segundos.

---

## 💬 Prompt Utilizado

```text
Crie um diagrama de fluxo detalhado para um aplicativo de comparação de preços de supermercado chamado "Conta-Certa", mostrando as seguintes etapas:

1. Entrada de Dados (Usuário): Tirar foto do cupom fiscal ou escanear QR Code da nota no aplicativo Lovable.
2. Processamento e Automação (Make + IA): O Make recebe a imagem, envia para o Gemini/ChatGPT para fazer a leitura OCR, extrair os itens, preços e datas, e normalizar os nomes dos produtos.
3. Armazenamento (Banco de Dados): Salvar os dados organizados no Supabase/Google Sheets nas tabelas de Compras e Itens.
4. Análise e Comparação (IA/Regras): Comparar o preço unitário dos produtos com o histórico de compras anteriores e calcular a variação percentual.
5. Saída e Feedback (Usuário): Exibir na tela do aplicativo o resumo da compra, o gráfico de histórico de preços e alertas de itens que subiram ou baixaram de valor.
```
## Passo a Passo de Execução no Whimsical
Acesse a[ página Whimsical](https://whimsical.com/workspace9765/MCWRi9paQjGPkRBq5ydQna)

1. Clique em Create New -> Board.

2. No menu lateral ou na área de trabalho, escolha a opção de Mind Map (Mapa Mental) ou Flowchart (Fluxograma).

3. Clique no ícone de estrelinhas (IA).

4. Cole o prompt acima na caixa de texto e dê Enter.

5. O Whimsical vai desenhar a estrutura visual inteira com as caixas e conexões automaticamente!

## Resultado Obtido

**Saída gerada:** Fluxograma com decisão de entrada (Foto vs. QR Code),
tratamento de erros (foto ruim), bifurcação das tabelas no banco de dados
e alertas de variação de preço (subiu, baixou ou estável).

**Arquivo de imagem salvo:** `projeto/Sprint-1/fluxo-conta-certa-whimsical.png`
