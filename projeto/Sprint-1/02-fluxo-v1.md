# 02 · Fluxo de Dados e Arquitetura: Conta-Certa (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 1 · Módulo 12: Desenhando o fluxo da sua solução**

---

##  1. Visão Geral do Fluxo

O projeto **Conta-Certa** opera sob a estrutura fundamental de automação:
**Input (Entrada) → Processamento (IA + Regras) → Output (Saída + Armazenamento)**.

```text
[ Usuária / App Lovable ] ──(Foto do Cupom / QR Code)──> [ Automação Make / N8N ]
                                                                   │
                                                                   ▼
[ Painel / Histórico ] <──(Dados Comparados)── [ Banco Supabase / Sheets ] <── [ Visão / OCR Gemini ]
```
## 2. Detalhamento das Etapas

### Etapa 1: Input (Entrada de Dados)

1.1 Ação da usuária:Tira uma foto do cupom fiscal impresso ou cola o link/QR Code da Nota Fiscal Eletrônica (NFC-e) na interface web.

1.2 Canal: App/Webapp construído no Lovable (vibe coding).

1.3 Dados capturados: Arquivo de imagem (.jpg/.png) ou string do QR Code.

### Etapa 2: Processamento (Visão, OCR e Padronização)

2.1 Gatilho (Trigger): O envio da imagem no Lovable aciona um webhook no Make / N8N.

2.2 Extração com IA (Google Gemini / ChatGPT Multimodal):
-   Visão Computacional: Lê os caracteres da imagem, mesmo amassada ou com sombra.
-   Identificação de Metadados: Captura Nome do Estabelecimento, Data da Compra e Valor Total.
-   Extração da Tabela de Itens: Mapeia a lista com [Código, Descrição Original, Quantidade, Valor Unitário, Valor Total].

2.3 Tratamento e Normalização (LLM):

-  Traduz abreviações do cupom fiscal para nomes amigáveis (ex.: "MANG ADEN KG" → "Manga Palmer KG").

-  Categoriza o item automaticamente (Ex.: Alimentação, Limpeza, Higiene, Hortifruti).

## Etapa 3: Output (Saída e Armazenamento)

3.1 Armazenamento: O Make insere os dados estruturados nas tabelas correspondentes do Google Sheets / Supabase:

-  Tabela_Compras: ID da Compra, Data, Mercado, Total.

-  Tabela_Itens: ID do Item, Categoria, Nome Normalizado, Preço Unitário, ID_Compra.

 3.2 Cálculo de Comparação: A aplicação verifica se o item já existe no histórico e calcula a variação percentual:

<img width="2172" height="724" alt="Image" src="https://github.com/user-attachments/assets/272215f1-6876-44f2-aa75-6cae6c444831" />

3.3 Interface da Usuária (Feedback Visual):

-  Exibição do resumo da nota cadastrada.

-  Alerta visual no Lovable: 🔴 Itens que subiram de preço, 🟢 Itens que baixaram, ⚪ Itens sem alteração.


### 3. Divisão de Papéis: Onde entra a IA vs. Onde entra o Humano

| Etapa do Fluxo | Responsável | Função Principal |
| :--- | :--- | :--- |
| **Captura do Cupom** | Humano | Tirar a foto visível ou escanear o QR Code. |
| **OCR e Estruturação** | IA (Gemini/ChatGPT) | Ler a imagem, extrair textos e normalizar nomes. |
| **Orquestração** | Automação (Make) | Mover os dados entre a IA, o banco de dados e a interface. |
| **Armazenamento** | Banco (Supabase/Sheets) | Guardar o histórico sem perda de dados. |
| **Validação Final** | Humano | Conferir se o valor total bate com o cupom e ajustar itens mal lidos, se houver. |

### 4. Registro no Whimsical / Mapas Mentais
-  Mapeamento lógico: Whimsical / Napkin AI para desenhar os nós da automação.

-  Estudo de documentos: NotebookLM para analisar estruturas do padrão de dados da NFC-e e NFe brasileira.

  <ElicitationsGroup message="Qual o próximo arquivo que gostaria de estruturar?">
  <Elicitation label="Criar o checklist de Ética, Privacidade e Viabilidade do Módulo 13 (projeto/03-viabilidade-e-etica-v1.md)" query="Vamos criar o checklist de viabilidade e ética (Módulo 13) para o Conta-Certa."/>
  <Elicitation label="Criar o prompt PACEF para leitura e extração das notas (prompts/01-ocr-nota-fiscal-pacef-v1.md)" query="Vamos criar o arquivo do prompt PACEF para extração do cupom fiscal e salvar na pasta prompts/."/>
  <Elicitation label="Criar o script de refinamento com feedback da IA para o Módulo 14 (projeto/04-refinamento-v1.md)" query="Vamos estruturar a etapa de refinamento da proposta com a IA para o Módulo 14."/>
</ElicitationsGroup>
