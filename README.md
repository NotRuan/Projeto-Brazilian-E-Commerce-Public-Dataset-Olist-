# 📊 Projeto BI — Análise do *Brazilian E-Commerce Public Dataset (Olist)*

Este projeto apresenta um dashboard executivo desenvolvido em **Power BI** utilizando o dataset público da **Olist**, com foco na performance de vendas, comportamento do cliente e qualidade da experiência (NPS e avaliações).  

<img width="1437" height="795" alt="Image" src="https://github.com/user-attachments/assets/e7fd6612-812e-4d9f-bac5-09de7fa17ae7" />

---

## 🎯 Objetivo do Projeto
Construir uma visão consolidada dos principais KPIs estratégicos de um ecossistema de e-commerce, permitindo que gestores acompanhem tendências, gargalos e oportunidades com um painel simples, direto e orientado a decisão.

---

## 📌 Principais KPIs Apresentados
- **Total de pedidos:** 99,4K  
- **Receita total:** R$ 1,6 Bi  
- **Ticket médio:** R$ 15,4K  
- **NPS Score:** 62,38  
- **Avaliação média:** 4,09 estrelas  

---

## 🔍 Principais Insights do Dashboard
- **São Paulo** é o estado com maior concentração de pedidos.  
- **Cartão de crédito** domina como principal forma de pagamento (77%).  
- Categorias **cama/mesa/banho** e **beleza/saúde** são líderes em receita.  
- A evolução temporal mostra **crescimento sólido entre 2016 e 2018**.  

---

## 🗂️ Estrutura do Dataset Utilizado
O dataset original contém diversas tabelas (CSV), sendo as principais:

- `orders.csv` — informações de pedidos  
- `order_items.csv` — itens de pedidos  
- `order_payments.csv` — métodos de pagamento  
- `order_reviews.csv` — avaliações e notas  
- `products.csv` — catálogo de produtos  
- `product_category_name_translation.csv` — tradução das categorias  
- `customers.csv` — dados do cliente  
- `sellers.csv` — vendedores  
- `geolocation.csv` — georreferenciamento por CEP  

![Image](https://github.com/user-attachments/assets/23ac1201-d0c7-4a81-b80b-9478e47b37b9)

---

## 🏗️ Arquitetura & Modelagem
O modelo de dados foi organizado em um **Star Schema** para garantir performance e clareza analítica:

### **Tabela Fato (Fato Vendas)**
Contém informações de vendas, valores, frete, itens, pagamento e datas — conectando todas as dimensões.

### **Tabelas Dimensão**
- **DimDate** — calendário completo  
- **DimCustomer** — atributos do cliente  
- **DimProduct** — categorias e características do produto  
- **DimSeller** — informações do vendedor  
- **DimPayment** — tipos de pagamento  
- **DimGeography** — UF, cidade e posição geográfica  

## Adicionar schema
---

## 🔧 Processo ETL (Power Query)

### **1. Ingestão**
Importação dos CSVs originais.

### **2. Limpeza**
- Padronização de colunas  
- Normalização de categorias  
- Remoção de duplicatas  
- Tratamento de nulos críticos  
- Conversão de datas e fusos  

### **3. Transformações**
- Merge de tabelas de pedidos, itens, pagamentos e produtos  
- Tradução de categorias através de `product_category_name_translation`  
- Cálculo de colunas importantes como:
  - Valor total por pedido  
  - Quantidade por item  
  - Valor total de pagamento  
- Criação de hierarquias geográficas

### **4. Feature Engineering**
- Criação de buckets (nome, peso, categorias)  
- Normalização de métodos de pagamento  
- Tabela calendário totalmente automatizada  

---

## 🧠 Métricas DAX Implementadas

### **Métricas Principais**
- Total de Pedidos  
- Receita Total  
- Ticket Médio  
- Avaliação Média  
- Crescimento MoM (Month over Month)  
- NPS calculado com base em reviews
