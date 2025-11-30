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
