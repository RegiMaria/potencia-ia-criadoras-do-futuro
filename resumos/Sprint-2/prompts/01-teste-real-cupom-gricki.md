# 01 · Teste Prático de OCR: Extração de Cupom Fiscal Real (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 2 · Módulos 05, 13 e 20: Validação Prática de Prompt, Visão Computacional e Teste com Dados Reais**

---

##  1. Objetivo do Teste

Validar a capacidade de extração de dados, Visão Computacional (OCR), padronização comercial e respeito à LGPD/privacidade do prompt **PACEF (v1.0)** utilizando uma foto de cupom fiscal real de supermercado.

---

##  2. Dados do Cupom Testado

* **Estabelecimento:** Supermercados Gricki Ltda (Ribeirão Preto - SP)
* **Data da Compra:** 26/09/2026 às 09:51
* **Total da Nota:** R$ 174,78 (17 itens)
* **Forma de Pagamento:** Cartão de Crédito
* **Condições Físicas da Imagem:** Cupom impresso completo, iluminação ambiente, com pequenos amassados e dados de autorização de maquininha/cartão expostos na parte inferior.

---

##  3. Prompt Executado (PACEF v1.0)

```text
[PAPEL]
Atue como um especialista em Visão Computacional, OCR e Análise de Dados Comerciais de Supermercados Brasileiros.

[AÇÃO]
Analise a imagem do cupom fiscal anexado (ou o texto da Nota Fiscal Eletrônica) e extraia todos os produtos comprados, seus preços unitários, quantidades e valores totais. Além disso, normalize as descrições dos produtos e categorize cada item.

[CONTEÚDO / CONTEXTO]
- O documento é um cupom fiscal/NFC-e de um supermercado brasileiro.
- Cupons fiscais usam abreviações agressivas (exemplo: "LT INTEGRAL ITAMB 1L" ou "MANG ADEN KG").
- É FUNDAMENTAL respeitar a LGPD e a privacidade da usuária: IGNORE e DESCONSIDERE qualquer informação sobre CPF, nome do consumidor, bandeira ou final do número do cartão de crédito/débito.
- Se a imagem estiver embaçada, cortada ou ilegível em algum ponto, informe explicitamente no campo de observações sem inventar dados.

[EXEMPLOS DE PADRONIZAÇÃO]
- Entrada no Cupom: "LEITE UHT INTEGRAL ITAMB 1L" -> Nome Normalizado: "Leite Integral Itambé 1L" | Categoria: "Laticínios"
- Entrada no Cupom: "DETERG YP NEUTRO 500ML" -> Nome Normalizado: "Detergentes Ypê Neutro 500ml" | Categoria: "Limpeza"
- Entrada no Cupom: "BANANA PRATA KG" -> Nome Normalizado: "Banana Prata KG" | Categoria: "Hortifruti"

[FORMATO DE SAÍDA]
Entregue o resultado estritamente em formato JSON válido, seguindo esta estrutura:

{
  "compra": {
    "estabelecimento": "Nome do Mercado",
    "data_compra": "AAAA-MM-DD",
    "valor_total_nota": 00.00,
    "leitura_com_sucesso": true,
    "observacoes": "Descreva aqui se houve alguma falha de leitura ou rasura"
  },
  "itens": [
    {
      "descricao_original": "TEXTO EXATO DO CUPOM",
      "nome_normalizado": "Nome Amigável Padronizado",
      "categoria": "Alimentação | Laticínios | Limpeza | Higiene | Hortifruti | Bebidas | Outros",
      "quantidade": 0,
      "preco_unitario": 00.00,
      "preco_total_item": 00.00
    }
  ]
}
```
## 4. Output / Resultado em JSON Gerado pela IA

```json
{
  "compra": {
    "estabelecimento": "SUPERMERCADOS GRICKI LTDA",
    "data_compra": "2026-09-26",
    "valor_total_nota": 174.78,
    "leitura_com_sucesso": true,
    "observacoes": "Leitura realizada com sucesso de todos os 17 itens do cupom fiscal. O CPF/CNPJ do consumidor não estava identificado no documento."
  },
  "itens": [
    {
      "descricao_original": "7898923109121 SOPINHA NIUDA CESCA PICADINHOS 200G",
      "nome_normalizado": "Sopinha Miúda Cecília Picadinhos 200g",
      "categoria": "Alimentação",
      "quantidade": 1,
      "preco_unitario": 6.99,
      "preco_total_item": 6.99
    },
    {
      "descricao_original": "7891000623008 ALIM CAO BIFINHO DOGUITOS 65G CARNE",
      "nome_normalizado": "Petisco para Cães Bifinho Doguitos 65g Carne",
      "categoria": "Outros",
      "quantidade": 1,
      "preco_unitario": 9.30,
      "preco_total_item": 9.30
    },
    {
      "descricao_original": "4239 COXA SOBRECOXA DALIA PCT kg",
      "nome_normalizado": "Coxa e Sobrecoxa Dália Pacote KG",
      "categoria": "Alimentação",
      "quantidade": 2.234,
      "preco_unitario": 10.90,
      "preco_total_item": 24.35
    },
    {
      "descricao_original": "423 PEITO FGO ADORO S/OSSO CONG PC kg",
      "nome_normalizado": "Peito de Frango Adoro sem Osso Congelado KG",
      "categoria": "Alimentação",
      "quantidade": 1.580,
      "preco_unitario": 19.90,
      "preco_total_item": 31.44
    },
    {
      "descricao_original": "1050 COUVE FLOR UN",
      "nome_normalizado": "Couve-Flor Unidade",
      "categoria": "Hortifruti",
      "quantidade": 1,
      "preco_unitario": 8.99,
      "preco_total_item": 8.99
    },
    {
      "descricao_original": "7891515531331 FRANGO FIGADO PERDIGAO PC 1kg",
      "nome_normalizado": "Fígado de Frango Perdigão Pacote 1kg",
      "categoria": "Alimentação",
      "quantidade": 1,
      "preco_unitario": 6.99,
      "preco_total_item": 6.99
    },
    {
      "descricao_original": "7891000109298 COOKIES NESTLE PASSATEMPO 60G",
      "nome_normalizado": "Cookies Nestlé Passatempo 60g",
      "categoria": "Alimentação",
      "quantidade": 1,
      "preco_unitario": 2.99,
      "preco_total_item": 2.99
    },
    {
      "descricao_original": "52 BANANA NANICA kg",
      "nome_normalizado": "Banana Nanica KG",
      "categoria": "Hortifruti",
      "quantidade": 1.030,
      "preco_unitario": 5.99,
      "preco_total_item": 6.17
    },
    {
      "descricao_original": "523 MANGA TOMMY kg",
      "nome_normalizado": "Manga Tommy KG",
      "categoria": "Hortifruti",
      "quantidade": 1.090,
      "preco_unitario": 5.99,
      "preco_total_item": 6.53
    },
    {
      "descricao_original": "7898051550024 LEITE PAST SERRALAT TP B 1L",
      "nome_normalizado": "Leite Pasteurizado Serralat Tipo B 1L",
      "categoria": "Laticínios",
      "quantidade": 1,
      "preco_unitario": 5.39,
      "preco_total_item": 5.39
    },
    {
      "descricao_original": "7891025121923 IOG DANONE LIQ 1250G MORANGO",
      "nome_normalizado": "Iogurte Danone Líquido 1250g Morango",
      "categoria": "Laticínios",
      "quantidade": 1,
      "preco_unitario": 18.59,
      "preco_total_item": 18.59
    },
    {
      "descricao_original": "82 BATATA GRAUDA kg",
      "nome_normalizado": "Batata Graúda KG",
      "categoria": "Hortifruti",
      "quantidade": 0.960,
      "preco_unitario": 6.99,
      "preco_total_item": 6.71
    },
    {
      "descricao_original": "7898963270188 OVO BRANCO GRANJA ENG GRANDE 20UN",
      "nome_normalizado": "Ovos Brancos Granja Engenho Grande 20 Unidades",
      "categoria": "Alimentação",
      "quantidade": 1,
      "preco_unitario": 14.90,
      "preco_total_item": 14.90
    },
    {
      "descricao_original": "539 ABOBRINHA PAULISTA kg",
      "nome_normalizado": "Abobrinha Paulista KG",
      "categoria": "Hortifruti",
      "quantidade": 1.245,
      "preco_unitario": 5.99,
      "preco_total_item": 7.46
    },
    {
      "descricao_original": "1184 VERDURAS FOLHAS UN",
      "nome_normalizado": "Verduras em Folhas Unidade",
      "categoria": "Hortifruti",
      "quantidade": 1,
      "preco_unitario": 6.99,
      "preco_total_item": 6.99
    },
    {
      "descricao_original": "50 BANANA MARMELO kg",
      "nome_normalizado": "Banana Marmelo KG",
      "categoria": "Hortifruti",
      "quantidade": 0.540,
      "preco_unitario": 9.98,
      "preco_total_item": 5.39
    },
    {
      "descricao_original": "195 CHUCHU kg",
      "nome_normalizado": "Chuchu KG",
      "categoria": "Hortifruti",
      "quantidade": 0.935,
      "preco_unitario": 5.99,
      "preco_total_item": 5.60
    }
  ]
}
```
## 5. Análise de Desempenho & Conclusões

| Critério de Avaliação | Resultado | Observações Práticas |
|---|:---:|---|
| **Acurácia do OCR (Visão)** | 🟢 **100%** | Todos os 17 itens, preços e quantidades por peso (KG) foram lidos perfeitamente. |
| **Abreviações & Normalização** | 🟢 **100%** | Exemplo: converteu `"LEITE PAST SERRALAT TP B 1L"` em `"Leite Pasteurizado Serralat Tipo B 1L"`. |
| **Validação de Privacidade / LGPD** | 🟢 **100%** | Os dados da autorização do cartão de crédito (`MASTER CARD - CREDITO ************0200`) expostos no papel foram **ignorados** no JSON final. |
| **Compatibilidade com Webhook** | 🟢 **100%** | A saída foi entregue estritamente em JSON válido, pronta para consumo em ferramentas como Make/N8N. |
