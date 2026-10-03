# 03 · Viabilidade Técnica, Ética e Governança: Conta-Certa (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 1 · Módulo 13: A IA dá conta? Validando a viabilidade da sua solução**

---

## 🔍 1. Avaliação de Viabilidade Técnica & Operacional

| Pergunta-Chave | Resposta & Diagnóstico | Ação Mitigatória |
|---|---|---|
| **A IA tem o que precisa para funcionar bem?** | **Parcialmente.** A IA multimodal (Gemini/ChatGPT) possui excelente OCR, mas cupons fiscais rasurados, dobrados ou apagados podem gerar falhas na extração. | Adicionar uma instrução no app para a usuária tirar fotos bem iluminadas e um passo de conferência humana antes de salvar. |
| **É fácil integrar os sistemas?** | **Sim.** A integração via Webhook no Make/N8N conectando o Lovable com as APIs das LLMs e o Google Sheets/Supabase é viável e *low-code*. | Testar os fluxos com webhooks gratuitos antes de rodar em escala. |
| **Existe restrição de linguagem ou cultura?** | **Sim.** Cupons fiscais brasileiros usam abreviações locais severas (ex.: `"LT INTEGRAL ITAMB 1L"` ou `"MANG ADEN KG"`). | Treinar o prompt com exemplos (few-shot prompting) das abreviações de supermercados brasileiros mais comuns. |

---

## 🔒 2. Privacidade, Governança e Proteção de Dados (LGPD)

| Item de Atenção | Risco Identificado | Diretriz de Governança |
|---|---|---|
| **Dados Pessoais Identificáveis (PII)** | Cupons fiscais frequentemente contêm o **CPF do consumidor**, **nome completo** ou o **número do cartão de crédito** (últimos dígitos). | **Remoção de PII:** O prompt de extração instrui explicitamente a IA a ignorar e desconsiderar CPF, nome e dados de pagamento da leitura. |
| **Privacidade dos Dados de Consumo** | Vazamento de hábitos de compra ou dados financeiros domésticos em ferramentas públicas de IA. | Usar modelos que não utilizem dados de API/enterprise para treinamento público (como API do Gemini/OpenAI ou NotebookLM). |
| **Sigilo Financeiro** | Subir documentos financeiros em chats gratuitos sem controle. | Não realizar upload de extratos bancários completos ou faturas de cartão; restringir o uso exclusivamente a cupons de supermercado. |

---

## ⚖️ 3. Avaliação de Riscos Éticos e Prejuízos ao Usuário

### As 4 Perguntas-Chave do Módulo 13:

1. **A IA tem o que precisa para funcionar bem?**  
   *Sim*, desde que a imagem do cupom esteja legível e o prompt contenha o contexto das abreviações comerciais brasileiras.

2. **Quem vai usar a solução entende como ela funciona?**  
   *Sim*. A usuária entende que a IA lê a nota e organiza os dados, sabendo que se trata de uma ferramenta de apoio à decisão financeira familiar.

3. **Alguém pode ser prejudicado se a IA errar?**  
   *O risco é baixo, mas existe.* Se a IA ler o preço do leite como R$ 50,00 em vez de R$ 5,00, a média do gráfico ficará distorcida, gerando um alerta falso de alta de preços.  
   * **Solução:** O app exibirá uma tela de confirmação *"Confirme os valores extraídos antes de salvar no seu histórico"*.

4. **A solução respeita princípios de ética e privacidade?**  
   *Sim*. O projeto é focado unicamente na gestão orçamentária doméstica, sem compartilhamento de dados com terceiros ou uso comercial dos hábitos de consumo.

---

## 📝 4. Matriz de Decisão: A IA dá conta?

> **Conclusão de Viabilidade:** **APROVADO COM RESSALVAS** 🟢
> 
> A solução é viável tecnicamente com a arquitetura proposta (Lovable + Make + Gemini/ChatGPT). Para garantir a precisão sem prejuízo ao orçamento da usuária, **a validação humana final é obrigatória** antes da gravação definitiva no banco de dados.

---

## 🔄 5. Checklist de Verificação Antes de Prototipar

- [ ] O prompt ignora CPFs e números de cartão.
- [ ] Existe um fallback (tratamento de erro) se a foto estiver ilegível.
- [ ] A usuária pode editar um valor extraído incorretamente antes de salvar.
- [ ] As diretrizes de LGPD e não-treinamento de dados da API foram respeitadas.

> Marcaremos esses tópico posteriormente.
