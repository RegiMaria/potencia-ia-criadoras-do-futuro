<p align="center">
  <img
    width="100"
    height="100"
    alt="Banner"
    src="https://github.com/user-attachments/assets/821167d0-128e-4da7-bec6-2035ceb97547" 
  />
</p>


# 06 · Da Ideia ao Protótipo: Estruturando o Conta-Certa

**Bloco 2 & 3 · Trilha Criadoras do Futuro com IA · 2026**

---

##  Objetivo do Bloco

Aprender a mapear tipos de IA, estruturar propostas de valor,
desenhar fluxos lógicos e construir protótipos/MVPs rápidos de
comunicação, visual e automação para validar ideias com dados reais.

---

## O Caminho do Bloco

| Módulo / Etapa | Conceito & Aplicação Prática |
| :--- | :--- |
| **06 & 09 · Tipos de IA** | **IA Híbrida / Automatizada:** Combina Visão Computacional/OCR (leitura de foto de cupom ou QR Code), IA Generativa (extração de dados e normalização de nomes de produtos) e banco de dados para comparação de valores. |
| **10 · Estrutura da Proposta** | **Escopo da Ideia:** Define o Problema (inflação doméstica desacompanhada), Benefício (rastreamento de variação de preços %), Ferramentas (Lovable + Make + Gemini/ChatGPT) e Função da IA (OCR + cálculo de variações). |
| **12 · Fluxo da Solução** | **Arquitetura Lógica:** Mapeia o caminho Input (foto/QR Code) $\rightarrow$ Processamento (extração de itens, preços unitários e data via IA) $\rightarrow$ Output (tabela comparativa e alertas de variação). |
| **17 · Comunicação** | **Tom de Voz do Assistente:** Define a mensagem de feedback e interação com a usuária: *"Análise do seu cupom concluída! Identifiquei 3 itens que subiram de preço desde a última compra."* |
| **18 · Protótipo Visual** | **Interface com Vibe Coding:** Uso do Lovable para criar em 5 minutos a tela web/mobile com botão de envio de foto da nota e painel de histórico de produtos. |
| **19 · Automação** | **Fluxo Low-Code:** Configuração no Make ou N8N para orquestrar o envio da imagem da nota para o Gemini/ChatGPT e salvar os dados no Google Sheets ou Supabase. |
| **20 & 21 · Validação & Iteração** | **Teste Prático & Feedback:** Testar com 3 cupons fiscais reais do cotidiano, analisar acertos/erros de OCR com pessoas e personas na IA e gerar a versão V2 refinada. |

---

##  As Três Trilhas da Formação

| Trilha | Nível | Objetivo |
| :--- | :--- | :--- |
| **1 - Exploradoras da Inteligência Artificial** | Iniciante | Desmistificar a IA e desenvolver letramento digital |
| **2 - Transformadoras do Presente com IA** | Intermediária | Desenvolver habilidades práticas de IA no trabalho |
| **3 - ✨ Criadoras do Futuro com IA** | Avançada | Desenvolver soluções com IA e liderar iniciativas transformadoras |

> **Nota:** A minha é a **Trilha 3**.

---

## 💡 Frase-chave

> *"A ferramenta certa no fluxo certo transforma um problema complexo em uma solução simples e acionável."*

---

## 💭 Minha Reflexão

### Antes do bloco: o que eu pensava sobre construir uma solução completa de IA
Acreditava que para criar um sistema capaz de ler notas fiscais e comparar preços mês 
a mês seria necessário esperar meses acumulando dados reais, ter conhecimentos avançados de 
programação para conectar bancos de dados e dominar modelos complexos de Visão Computacional do zero.

### Depois do bloco: o que mudou na forma como eu vejo e uso a IA
Percebi que não preciso esperar meses de compras reais para validar o projeto: 
posso prototipar o **Conta-Certa** em dias usando cupons antigos que já tenho em casa.
Aprendi a integrar ferramentas de *vibe coding* (Lovable) com orquestradores *low-code* (Make) e
modelos de IA multimodal (Gemini/ChatGPT). Entendi que a inteligência artificial não atua sozinha, 
mas sim como um ecossistema híbrido onde o input da usuária e a validação humana mantêm a precisão e o controle da solução.

---

## Aplicação no Meu Projeto: Conta-Certa

*Como ficou a aplicação prática para o problema de finanças domésticas?*

| Pilar do Projeto | Detalhamento no Conta-Certa |
| :--- | :--- |
| **Problema** | Não consigo comparar os preços das minhas compras de mercado mês a mês porque as informações ficam espalhadas em papéis e PDFs. |
| **Pergunta para a IA** | Como a IA pode ler minhas notas fiscais (OCR), extrair a lista de produtos com seus preços unitários e me mostrar quais itens ficaram mais caros em relação ao mês anterior? |
| **Tipo de Solução** | **Híbrida:** Visão Computacional (OCR da foto) + LLM (Normalização de nomes abreviados de produtos) + Automação Make (envio dos dados para o banco). |
| **MVP / Protótipo** | Interface no Lovable para upload de foto da nota + leitura direta via Gemini + planilha de histórico no Google Sheets. |

---

➡️ **Registros do Projeto:** [`projeto/01-proposta-v1.md`](https://github.com/RegiMaria/potencia-ia-criadoras-do-futuro/blob/main/projeto/Sprint-1/01-proposta-v1.md) · [`projeto/02-fluxo-v1.md`](https://github.com/RegiMaria/potencia-ia-criadoras-do-futuro/blob/main/projeto/Sprint-1/02-fluxo-v1.md) ·[ `prompts/02-gerar-fluxo-whimsical-v1.md`](https://github.com/RegiMaria/potencia-ia-criadoras-do-futuro/blob/main/resumos/Sprint-1/prompts/04-diagrama-fluxo.md)
