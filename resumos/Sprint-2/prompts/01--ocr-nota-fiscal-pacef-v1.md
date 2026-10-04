# 01 · Prompt PACEF: Leitura e Extração de Cupom Fiscal (v1.0)

> **Projeto Prático · Trilha Criadoras do Futuro com IA · 2026**  
> **Sprint 2 · Módulos 04, 05 e 14: Framework PACEF, Engenharia de Prompts e OCR Multimodal**

---

## 📌 Contexto & Objetivo
Este prompt foi desenvolvido no framework **PACEF** para ler imagens de cupons fiscais brasileiros (ou dados do QR Code/NFC-e), ignorar dados sensíveis de privacidade (CPF/Cartão), padronizar descrições de produtos comercialmente abreviadas e extrair a tabela de itens em formato JSON estruturado para envio via Make/API.

---

## 📄 Prompt PACEF (Para Copiar e Usar)

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
