# 01 · Proposta de Solução: Conta-Certa (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 2 · Módulo 10: De ideia à solução: estruturando sua proposta**

---

## 1. Problema & Oportunidade

Os preços dos produtos de mercado sofrem variações constantes devido à inflação e sazonalidades.
No entanto, as informações sobre esses custos ficam dispersas em cupons fiscais impressos ou notas fiscais eletrônicas.

* **Sintoma:** Sensação constante de que as compras de mercado estão mais caras a cada mês.
* **Problema real:** Falta de dados organizados e centralizados sobre a variação do preço unitário dos produtos consumidos rotineiramente.
* **Oportunidade:** Usar inteligência artificial com visão computacional e extração de dados para ler notas fiscais automaticamente, criar um histórico estruturado de preços e apontar variações sem exigir digitação manual.

---

## 2. Benefícios & Persona Impactada

* **Persona principal:** Famílias e pessoas responsáveis pela gestão financeira do lar que buscam previsibilidade no orçamento doméstico.
* **Benefícios de uso:**
  * **Economia de tempo:** Extração automática dos itens e valores a partir da foto da nota fiscal ou leitura do QR Code.
  * **Clareza de dados:** Visualização simples das variações de preço (%) mês a mês por produto e por categoria (alimentação, limpeza, higiene).
  * **Poder de decisão:** Alertas sobre produtos que subiram acima da média, ajudando na substituição de marcas ou na escolha do estabelecimento mais vantajoso.

---

## 3. Arquitetura da Solução & Ferramentas

| Componente | Ferramenta Escolhida | Papel no Projeto |
|---|---|---|
| **Interface (Front-end)** | **Lovable** (*vibe coding*) | Interface web/mobile para upload da imagem da nota, envio de links e visualização dos gráficos/tabelas comparativas. |
| **Visão Computacional & OCR** | **Google Gemini / ChatGPT** | Leitura da foto do cupom fiscal, extração de texto e interpretação dos campos (estabelecimento, data, itens e valores). |
| **Automação (Integration)** | **Make / N8N** (*low-code*) | Orquestração do fluxo de dados: recebe a foto da interface, envia para a LLM processar e salva as informações organizadas. |
| **Banco de Dados (Back-end)** | **Google Sheets / Supabase** | Armazenamento seguro e estruturado do histórico de compras e tabela de preços por item. |

---

## 4. Função Exata da IA

A Inteligência Artificial atuará como uma **solução híbrida** (Visão + Extração + Automação):

1. **OCR e Visão Computacional:** Ler o texto contido na imagem do cupom fiscal ou na Nota Fiscal Gaúcha/Paulista/NFC-e, mesmo com variações de iluminação ou alinhamento.
2. **Padronização de Nomes:** Normalizar as descrições abreviadas dos estabelecimentos (ex.: converter `"LT INTEGRAL ITAMB 1L"` para `"Leite Integral Itambé 1L"`).
3. **Classificação e Análise:** Categorizar cada item automaticamente e comparar o valor unitário atual com a média histórica do mesmo item em compras passadas.

---

## 5. Próximos Passos (Evolução do Projeto)

- [ ] **v1.0 (Atual):** Estruturação da proposta inicial e validação dos objetivos.
- [ ] **v1.1:** Mapeamento do fluxo de dados completo - *Input → Processamento → Output* (Módulo 12).
- [ ] **v1.2:** Validação técnica, ética e governança de dados sensíveis da nota (Módulo 13).
- [ ] **v2.0:** Refinamento da proposta e criação do prompt PACEF para extração de OCR (Módulo 14).
- [ ] **v3.0:** Prototipagem visual no Lovable e testes com cupons reais (Módulo 16+).
