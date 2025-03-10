# 🛒 Análise de Preços no iFood - Projeto de Ciência de Dados  

Este repositório documenta meu projeto de análise de preços de supermercados no iFood. Desde a coleta e o processamento dos dados até a análise e visualização, utilizei web scraping, técnicas de ETL, bancos de dados e ferramentas de visualização de dados.  

---

## 📌 1. Introdução  

### 🎯 Objetivo  
O objetivo deste projeto foi analisar os preços dos produtos vendidos em supermercados pelo iFood, o maior aplicativo de delivery do Brasil. Para isso, utilizei técnicas de web scraping para coletar dados diretamente da plataforma, realizei o processamento dos dados e criei visualizações informativas.  

### 🚀 Tecnologias Utilizadas  
- **Python** (requests, pandas, matplotlib, SQLAlchemy, etc.)  
- **MySQL** (armazenamento de dados)  
- **AWS** (banco de dados na nuvem)  
- **Tableau** (visualização de dados)  

---

## 🔍 2. Coleta de Dados  

### 🕵️‍♂️ 2.1. Como o iFood Funciona  

Para entender como o iFood exibe os supermercados e produtos, utilizei a ferramenta **Inspecionar Elemento** no navegador (aba **Network**) para encontrar as APIs usadas pelo site.  

✅ **Principais Descobertas:**  
- O iFood utiliza **Google Maps** para converter endereços em coordenadas.  
- O site exibe supermercados disponíveis com base na distância do cliente e nas preferências do mercado.  
- Cada supermercado possui um **ID único**.  

🖼️ **Inspecionando o site do iFood**  
![Screenshot](./img/inspecionar_elemento.png)  

---

### 🌎 2.2. Obtendo Coordenadas  

Para acessar supermercados em todo o Brasil, precisei de coordenadas para todas as cidades. Cidades maiores exigiram múltiplas coordenadas.  

📂 **Resultado:**  
- Um arquivo CSV com **7267 linhas**, cobrindo grande parte do Brasil.  

🖼️ **Arquivo CSV com coordenadas**  
![Screenshot](./img/coordenadas.png)  

---

## ⚙️ 3. Extração e Processamento dos Dados  

Após enviar as coordenadas para o iFood, recebi listas de supermercados e coletei os produtos vendidos por cada um.  

❗ **Desafios:**  
- A resposta da API continha **tags desatualizadas e irrelevantes**.  
- Usei técnicas de **data mining e ETL** para limpar os dados.  

✅ **Resultado:**  
- Dados organizados incluindo:  
  - **Nome do produto**  
  - **Categoria (corredor)**  
  - **Preço**  
  - **ID do supermercado**  

🖼️ **Dados brutos vs. processados**  
![Screenshot](./img/datas_comparison_br.png)  

---

## 🗄️ 4. Armazenamento no Banco de Dados  

Armazenei os dados no **MySQL**, tanto localmente quanto na **AWS**.  

📊 **Estatísticas do Banco de Dados:**  
- **Mais de 15 milhões de linhas** coletadas.  
- **3791 supermercados** registrados.  

🖼️ **Banco de Dados**  
![Screenshot](./img/mysql_example.png)  
<img src="./img/database_info.png" width="800">

---

## 📊 5. Visualização dos Dados  

Utilizei **Python e Tableau** para criar gráficos e entender a distribuição dos preços.  

🖼️ **Exemplos de visualizações criadas**  
![Screenshot](./img/distribuição_corredor.png)  
![Screenshot](./img/distribuicao_precos.png)  
![Screenshot](./img/preco_medio_sp.png)  
![Screenshot](./img/quantidade_mercados_estado.png) 

---

## 🎯 6. Conclusões

Acredito que o iFood poderia investir mais na expansão de sua rede de supermercados, buscando cadastrar estabelecimentos de diferentes estados. Atualmente, há regiões com apenas 1, 3 ou até 0 supermercados registrados, o que limita a oferta para os consumidores. Além disso, a organização do cadastro de produtos poderia ser aprimorada. Muitos itens aparecem fora das categorias esperadas, como no caso de combos que estão posicionados em corredores inadequados, dificultando a busca e a navegação dos usuários. Essas melhorias poderiam proporcionar uma experiência mais fluida e abrangente para os consumidores.

Os corredores mais caros são os de Bebidas Alcoólicas, o que já era esperado, pois existem bebidas de valores muito altos, tambem podemos ver que a maioria dos produtos se concentra entre R$ 8,00 e R$ 20,00. Existem diversos outliers em todos os corredores, o que pode ser explicado pelo fato de que muitos supermercados colocam produtos em alta quantidade, como, por exemplo, combos, fora do corredor de combos. No entanto, em breve, poderei filtrar isso com machine learning. Fico curioso para ver como esses gráficos estarão diferentes em alguns meses.


Como podemos ver no último gráfico, diversos estados têm poucos supermercados disponíveis no iFood, tornando impossível analisar a média de preços verdadeira por estados usando apenas os dados do iFood. Por isso, estou desenvolvendo uma forma de conseguir mais supermercados nesses estados, provavelmente utilizando os sites oficiais dos supermercados. Isso também permitirá comparar os preços disponíveis no iFood com os encontrados nesses sites, e futuramente utilizar Machine Learning para prever preços.  

Este projeto demonstrou técnicas de **web scraping, ETL, gerenciamento de banco de dados e visualização de dados** para analisar preços no iFood. Mas ainda é um projeto em andamento, irei atualizar as técnicas e análises com o tempo.

🚀 **Atualizações futuras:**
- Comparar preços de produtos da cesta básica por estado.
- Automatizar a atualização dos dados.  
- Encontrar novas fontes para obter mais supermercados.  
- Aplicar machine learning para prever preços.  
