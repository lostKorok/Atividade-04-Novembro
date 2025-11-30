# 📚 Livraria Saber - Implementação e Manipulação de Dados SQL (Atividade 04)

---

## 🎯 Objetivo do Projeto

Este projeto visa a **implementação e manipulação de um banco de dados relacional** (`livraria_saber`) utilizando a **Linguagem de Consulta Estruturada (SQL)**, com foco em comandos DML (**Data Manipulation Language**).

O trabalho integra:
* **Modelagem Lógica** de um mini-mundo de livraria e papelaria.
* Práticas de **Desenvolvimento de Software** e **Versionamento (Git/GitHub)**.
* Garantia da **Integridade Referencial** dos dados através de chaves estrangeiras (Foreign Keys).

---

## 🧠 Ganhos de Aprendizagem (Taxonomia de Bloom e Fink)

| Taxonomia de Bloom | Taxonomia de Fink |
| :--- | :--- |
| **Aplicar**: Executar comandos SQL para manipulação de dados. | **Aplicação**: Uso de ferramentas reais (MySQL Workbench/PGAdmin). |
| **Criar**: Desenvolver scripts SQL completos e bem estruturados. | **Integração**: Combinar modelagem lógica e integridade com DML. |
| | **Aprender a Aprender**: Lidar com erros de sintaxe e buscar soluções. |

---

## 🛠️ Tecnologias e Ferramentas

* **SGBD**: **MySQL** (ou compatível, como PostgreSQL).
* **Linguagem**: **SQL** (Structured Query Language).
* **Ferramenta de Desenvolvimento**: **MySQL Workbench** / **DBeaver** / Outro cliente SQL.
* **Versionamento**: **Git** e **GitHub**.

---

## 📂 Estrutura do Repositório

O repositório contém os seguintes arquivos SQL, que formam a base de dados da livraria:

| Arquivo SQL | Conteúdo | Observação |
| :--- | :--- | :--- |
| `livraria_saber_**schema_full**.sql` | Script completo de criação do DB e tabelas. | Contém todos os `CREATE TABLE` e `INSERT` iniciais (DDL e DML). |
| `livraria_saber_**autor**.sql` | `CREATE TABLE` e `INSERT` para a tabela **autor**. | |
| `livraria_saber_**cliente**.sql` | `CREATE TABLE` e `INSERT` para a tabela **cliente**. | |
| `livraria_saber_**editora**.sql` | `CREATE TABLE` e `INSERT` para a tabela **editora**. | |
| `livraria_saber_**fornecedor**.sql` | `CREATE TABLE` e `INSERT` para a tabela **fornecedor**. | |
| `livraria_saber_**livro**.sql` | `CREATE TABLE` e `INSERT` para a tabela **livro**. | |
| `livraria_saber_**papelaria**.sql` | `CREATE TABLE` e `INSERT` para a tabela **papelaria**. | |
| `livraria_saber_**vendedor**.sql` | `CREATE TABLE` e `INSERT` para a tabela **vendedor**. | **Necessário** criar/incluir. |
| `livraria_saber_**venda**.sql` | `CREATE TABLE` e `INSERT` para a tabela **venda**. | Depende de `cliente` e `vendedor`. |
| `livraria_saber_**item_venda**.sql` | `CREATE TABLE` e `INSERT` para a tabela **item_venda**. | Depende de `venda`, `livro` e `papelaria`. |
| `livraria_saber_**dml_exemplos**.sql` | Script de manipulação de dados (**DML**). | Contém `SELECT`, `UPDATE` e `DELETE` solicitados. |

> **Nota**: Para recriar o banco do zero, utilize o arquivo de `schema_full` ou combine os arquivos individuais **na ordem de dependência** para garantir a ordem correta das **Foreign Keys**.

---

## ⚙️ Instruções de Execução

Siga os passos para configurar e executar o projeto:

### 1. Configuração do Ambiente
Instale o **MySQL Server** e o **MySQL Workbench** (ou seu cliente SQL preferido).

### 2. Criação do Banco de Dados
Crie o banco de dados `livraria_saber` em seu SGBD:

```sql
CREATE DATABASE livraria_saber;
USE livraria_saber;

3.	Criação e População de Tabelas (DDL e DML - INSERT):
o	Execute o script principal (livraria_saber_schema_full.sql - assumindo que você combinou todos os CREATE TABLE e INSERT iniciais em um único arquivo, se não, execute-os na ordem de dependência) ou execute os arquivos individuais na seguinte ordem para respeitar as chaves estrangeiras:
1.	autor.sql
2.	cliente.sql
3.	editora.sql
4.	fornecedor.sql
5.	vendedor.sql (Necessário script!)
6.	livro.sql (Depende de editora)
7.	papelaria.sql (Depende de fornecedor)
8.	livro_autor.sql (Depende de livro e autor)
9.	venda.sql (Depende de cliente e vendedor)
10.	item_venda.sql (Depende de venda, livro e papelaria)
4.	Manipulação de Dados (DML - Consultas/Atualizações/Exclusões):
o	Execute o script livraria_saber_dml_exemplos.sql para testar as consultas, atualizações e exclusões solicitadas na atividade.
________________________________________
📝 Exemplos de Comandos DML
O script livraria_saber_dml_exemplos.sql demonstra a manipulação de dados.
🔍 Consultas (SELECT)
Demonstração de consultas complexas, utilizando junções, agrupamento e ordenação.
SQL
-- 1. Listar o título dos livros e o nome de seus respectivos autores. (JOIN)
SELECT
    l.titulo,
    a.nome AS autor_nome
FROM livro l
JOIN livro_autor la ON l.id_livro = la.id_livro
JOIN autor a ON la.id_autor = a.id_autor
ORDER BY l.titulo;

-- 2. Calcular o valor total de todas as vendas e agrupar por forma de pagamento, mostrando o total geral no final. (GROUP BY, SUM)
SELECT
    forma_pagamento,
    SUM(valor_total) AS total_por_pagamento
FROM venda
GROUP BY forma_pagamento WITH ROLLUP;

-- 3. Encontrar o nome do cliente que realizou a compra de maior valor. (Subconsulta ou ORDER BY/LIMIT)
SELECT
    c.nome AS cliente_maior_compra,
    v.valor_total
FROM venda v
JOIN cliente c ON v.id_cliente = c.id_cliente
ORDER BY v.valor_total DESC
LIMIT 1;

-- 4. Listar nome e preço de todos os itens de papelaria na categoria 'Escolar' com estoque menor que 100, ordenados por preço. (WHERE, ORDER BY)
SELECT
    nome,
    preco,
    quantidade_estoque
FROM papelaria
WHERE categoria = 'Escolar' AND quantidade_estoque < 100
ORDER BY preco DESC;
✍️ Atualização de Dados (UPDATE)
Atualizações que alteram o estado de colunas específicas.
SQL
-- 1. Aumentar o preço do livro "O Enigma do Tempo" (id_livro = 1) em 10%.
UPDATE livro
SET preco = preco * 1.10
WHERE id_livro = 1;

-- 2. Atualizar o cargo do vendedor "Maria Souza" para "Consultor Pleno".
UPDATE vendedor
SET cargo = 'Consultor Pleno'
WHERE nome = 'Maria Souza';

-- 3. Aumentar a quantidade em estoque em 50 unidades para todos os itens de papelaria da marca '3M'.
UPDATE papelaria
SET quantidade_estoque = quantidade_estoque + 50
WHERE marca = '3M';
🗑️ Exclusão de Dados (DELETE)
Exclusões que respeitam a integridade referencial (FOREIGN KEY).
SQL
-- 1. Deletar a Caneta Gel Azul (id_papelaria = 2), pois não está relacionada a nenhum item de venda com ON DELETE RESTRICT (Verificar a FK, se for RESTRICT, terá que deletar item_venda primeiro).
-- Se a FK em item_venda_ibfk_3 for ON DELETE RESTRICT, a linha abaixo falhará se houver um item_venda com id_papelaria=2.
-- O script item_venda_ibfk_3 no schema é ON DELETE RESTRICT.
-- Solução: Remover o item_venda dependente primeiro.
DELETE FROM item_venda WHERE id_papelaria = 2; -- Remove a dependência
DELETE FROM papelaria WHERE id_papelaria = 2; -- Agora o item pode ser excluído

-- 2. Deletar o fornecedor "Fornecedora Papel Ltda" (id_fornecedor = 1).
-- Também possui restrição (RESTRICT) em papelaria.
-- Primeiro, atualiza os produtos para um fornecedor "inativo" (ou outro fornecedor) se o DELETE não for permitido.
-- ALTERAR PARA TESTE: A FK de 'papelaria' para 'fornecedor' é RESTRICT, então a exclusão do fornecedor falhará se houver produtos.
-- Se fosse permitido (ex: não há produtos):
-- DELETE FROM fornecedor WHERE id_fornecedor = 1; -- **Isso falhará devido à FK**

-- 3. Deletar o cliente "Felipe Mendes" (id_cliente = 4), que não realizou nenhuma venda (Não possui registro na tabela 'venda').
DELETE FROM cliente WHERE id_cliente = 4;

