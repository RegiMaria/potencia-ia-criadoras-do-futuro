# 04 · Documentação da Automação Integrada (v1.1): n8n + Gemini + Lovable + Google Sheets

> **Projeto Conta-Certa · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 2: Integração de Ponta a Ponta, Diagnóstico de Erros e Validação de Fluxo**

---

##  1. Visão Geral da Versão 1.1

A versão 1.1 consolida a integração real entre a interface do usuário desenvolvida no **Lovable**, a automação do **n8n** publicada em ambiente cloud, o modelo multimodal **Google Gemini Flash Lite** e a persistência no **Google Sheets**.

```text
[ Front-End Lovable ] ──(POST Multipart/file)──> [ Webhook n8n ]
                                                        │
                                                        ▼
[ Google Sheets ] <──(Append Row)── [ Gemini Flash Lite (Vision OCR) ]

```

## 2. Configuração Atualizada do Fluxo no n8n

🟦 Nó 1: Webhook (Entrada de Dados)
- HTTP Method: POST

- Path: 63e7536a-c307-418e-9252-985e0f9c6bbb

- Response Mode: When Last Node Finishes

- Mapeamento do Arquivo: O Lovable envia o arquivo binário na propriedade de entrada chamada file.

🟪 Nó 2: Analyze an image (Google Gemini)

- Credential: Google Gemini API (AI Studio)

- Resource: Image

 Operation: Analyze Image

- Model: models/gemini-flash-lite-latest (Ajustado para evitar gargalo de cota no tier gratuito)

- Text Input: Prompt PACEF v1.0 (Extração estruturada em JSON + Regras LGPD)

- Input Type: Binary File(s)

- Input Data Field Name(s): file (Corrigido de data para file)

- Configuração de Resiliência (Settings):

    - Retry On Fail: Ligado
    - Max Tries: 3
    - Wait Between Tries: 3000 ms

🟩 Nó 3: Append row in sheet (Google Sheets)

- Operation: Append Row

- Document: Conta-Certa

- Sheet: Página1

🚨 3. Diário e Resolução de Problemas (Troubleshooting)

## 🔧 Gargalos Técnicos Resolvidos

Durante a integração da **v1.1**, identificamos e resolvemos **4 gargalos técnicos principais**:

| # | ❌ Erro Identificado | 🔍 Causa Raiz | ✅ Solução Aplicada |
|---|---|---|---|
| **1** | `The item has no binary field 'data'` | O Lovable envia a foto no campo binário `file`, mas o n8n procurava por `data`. | Alterado o parâmetro **Input Data Field Name(s)** no nó do Gemini para `file`. |
| **2** | `The resource you are requesting could not be found` | Seleção de identificador de modelo inexistente (`gemini-2.5-flash`). | Ajustado para a chave estável `models/gemini-flash-latest`. |
| **3** | `Service unavailable (503)` | Oscilação e estouro de limite de requisições no *Free Tier* do Gemini 1.5/2.0. | Alterado o modelo para `models/gemini-flash-lite-latest` e ativado o **Retry On Fail** com 3 tentativas. |
| **4** | `Texto {{ $json... }} salvo na planilha` | Mapeamento no nó do Google Sheets definido como texto fixo (*Fixed*) em vez de expressão dinâmica. | Ativação da chave de expressão **`fx`** em todos os campos mapeados do nó. |


## 📸 Evidências dos Gargalos

### 1️⃣ Campo binário incorreto

<p align="center">
  <img src="https://github.com/user-attachments/assets/82eb13a5-7f85-43bb-8c6b-f1d94d09dd10"
       alt="Erro de campo binário no n8n"
       width="800">
</p>

<p align="center">
  <strong>Erro:</strong> <code>The item has no binary field 'data'</code><br>
  O Lovable enviava a imagem no campo <code>file</code>, enquanto o n8n procurava por <code>data</code>.
</p>

---

### 2️⃣ Modelo Gemini não encontrado

<p align="center">
  <img src="https://github.com/user-attachments/assets/93bbe819-24c3-49f4-88b3-bd1dfceeb19e"
       alt="Erro de modelo Gemini não encontrado"
       width="800">
</p>

<p align="center">
  <strong>Erro:</strong> <code>The resource you are requesting could not be found</code><br>
  O identificador do modelo utilizado não estava disponível.
</p>

---

### 3️⃣ Serviço Gemini indisponível

<p align="center">
  <img src="https://github.com/user-attachments/assets/cd062008-9fc3-4098-adaf-dede4673ddba"
       alt="Erro 503 do Gemini"
       width="800">
</p>

<p align="center">
  <strong>Erro:</strong> <code>Service unavailable (503)</code><br>
  A solução foi utilizar o modelo <code>models/gemini-flash-lite-latest</code>
  e configurar <strong>Retry On Fail</strong> com 3 tentativas.
</p>

---

### 4️⃣ Expressão não interpretada no Google Sheets

<p align="center">
  <img src="https://github.com/user-attachments/assets/cc8e2238-bea5-4815-93f0-3008bc3b784b"
       alt="Erro de expressão no Google Sheets"
       width="800">
</p>

<p align="center">
  <strong>Erro:</strong> <code>Texto {{ $json... }} salvo na planilha</code><br>
  O campo estava configurado como <strong>Fixed</strong> em vez de expressão dinâmica.
</p>

---


<div align="center"> <img width="200" alt="Image" src="https://github.com/user-attachments/assets/52b55575-06bf-47c0-8419-746256e1523f" /> </div>






## 4. Evidência de Execução - Fluxo Completo

### 1️⃣ Interface Lovable - Envio da Imagem

<p align="center">
  <img src="https://github.com/user-attachments/assets/c0bcf6f8-f21a-4b8e-a0a2-4f4d4c5c08dd"
       alt="Interface do Lovable enviando imagem"
       width="800">
</p>

<p align="center">
  📤 <strong>Etapa 1:</strong> a interface do Lovable recebe a imagem do cupom fiscal
  e inicia o processamento.
</p>

---

### 2️⃣ Lovable - Envio Realizado com Sucesso

<p align="center">
  <img src="https://github.com/user-attachments/assets/b0f32482-102a-46e6-b8a9-0d4659e4394d"
       alt="Lovable enviando dados com sucesso"
       width="800">
</p>

<p align="center">
  ✅ <strong>Etapa 2:</strong> a imagem é enviada com sucesso para o fluxo de processamento.
</p>

---

### 3️⃣ n8n - Processamento Completo

<p align="center">
  <img src="https://github.com/user-attachments/assets/1ad805fd-db41-4704-8306-47f690d5526e"
       alt="Fluxo n8n executado com sucesso"
       width="850">
</p>

<p align="center">
  ⚙️ <strong>Etapa 3:</strong> o workflow do n8n executa todas as etapas de processamento
  com sucesso, desde o recebimento da imagem até a saída dos dados.
</p>

---

### 🔄 Fluxo Validado

<p align="center">

<strong>📷 Lovable</strong>
&nbsp; → &nbsp;
<strong>🔗 Integração</strong>
&nbsp; → &nbsp;
<strong>⚙️ n8n</strong>
&nbsp; → &nbsp;
<strong>🤖 Processamento</strong>
&nbsp; → &nbsp;
<strong>📊 Dados Estruturados</strong>

</p>


## 5. Próximos Ajustes para a Versão 1.2 (Pós-Sucesso)

1. Ajuste de Expressão (fx): Ativar o modo de expressão em todos os campos do nó do Google Sheets.

2. Desmembramento de Itens (Split Out): Inserir o nó de loop/split para transformar a array itens do JSON em 17 linhas individuais na planilha.

3. Formatação de Valores: Garantir que preços e quantidades sejam interpretados numericamente no Google Sheets para gráficos e dashboards.

<div align="center">

<img src="https://github.com/user-attachments/assets/e08b71b4-b342-44de-b0e4-cb2464b381a4" alt="Fluxo da integração v1.2" width="850"/>

<br><br>

<img src="https://github.com/user-attachments/assets/6f94e677-8dce-4a1e-8b66-3246c99ea06c" alt="Detalhes da integração v1.2" width="400"/>

</div>


