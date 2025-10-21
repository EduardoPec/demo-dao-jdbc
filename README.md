# 💾 Sistema de Acesso a Banco de Dados com JDBC e Padrão DAO

![Java](https://img.shields.io/badge/Java-17-orange?logo=openjdk)
![JDBC](https://img.shields.io/badge/JDBC-Database-blue)
![MySQL](https://img.shields.io/badge/MySQL-Relational%20Database-00758F?logo=mysql)
![License](https://img.shields.io/badge/license-MIT-blue)

## 📖 Sobre o Projeto

Este projeto tem como objetivo demonstrar o uso do **JDBC (Java Database Connectivity)** integrado ao **padrão de projeto DAO (Data Access Object)** para realizar operações de acesso e manipulação de dados em um **banco de dados relacional** (MySQL).

A aplicação exemplifica como estruturar um sistema de **camadas desacopladas**, separando regras de negócio, persistência e tratamento de exceções, utilizando boas práticas de programação em Java.

---

## 🧱 Estrutura do Projeto
```
src/
├── application/
│ ├── Program.java # Classe principal (testes e execução)
│ └── Program2.java # Classe auxiliar de testes
├── db/
│ ├── DB.java # Gerencia conexões com o banco
│ ├── DbException.java # Exceção personalizada
│ └── DbIntegrityException.java # Exceção específica para integridade referencial
├── model/
│ ├── entities/
│ │ ├── Department.java # Entidade Departamento
│ │ └── Seller.java # Entidade Vendedor
│ ├── dao/
│ │ ├── DepartmentDao.java # Interface DAO para Department
│ │ ├── SellerDao.java # Interface DAO para Seller
│ │ └── DaoFactory.java # Fábrica de DAOs
│ └── dao/impl/
│ ├── DepartmentDaoJDBC.java # Implementação JDBC de DepartmentDao
│ └── SellerDaoJDBC.java # Implementação JDBC de SellerDao
```

---

## ⚙️ Tecnologias Utilizadas

- ☕ **Java 17**
- 🧩 **JDBC (Java Database Connectivity)**
- 🗄️ **MySQL** como banco de dados
- 🧱 **Padrão DAO (Data Access Object)**
- 🧰 **Tratamento de exceções personalizadas**
- 📦 **Factory Pattern** para criação de DAOs
- 🧹 **Boas práticas de fechamento de recursos JDBC**

---

## 🚀 Funcionalidades

- 🔹 Inserir novos registros (`INSERT`)
- 🔹 Atualizar registros existentes (`UPDATE`)
- 🔹 Deletar registros (`DELETE`)
- 🔹 Buscar registro por ID (`SELECT WHERE`)
- 🔹 Listar todos os registros (`SELECT *`)
- 🔹 Buscar vendedores por departamento
- 🔹 Tratar exceções SQL de forma personalizada

---

## 🧩 Padrão DAO

O projeto aplica o **padrão DAO (Data Access Object)** para isolar as operações de persistência do restante da aplicação.  
Cada entidade possui sua interface e implementação JDBC correspondente.

Exemplo de organização:

- SellerDao.java → Interface de operações
- SellerDaoJDBC.java → Implementação JDBC concreta
- DaoFactory.java → Fábrica responsável por instanciar DAOs


---

## ⚠️ Tratamento de Exceções

Foram criadas classes personalizadas para lidar com erros relacionados ao banco de dados:

- `DbException` → exceções genéricas de SQL  
- `DbIntegrityException` → violações de integridade referencial (ex.: ao deletar um departamento com vendedores vinculados)

---

## 🧰 Dependências

As bibliotecas utilizadas são gerenciadas manualmente (sem Maven).  
Para compilar e rodar, é necessário incluir o **driver JDBC do MySQL** (`mysql-connector-j.jar`) no classpath.

---

## 💾 Banco de Dados MySQL

- **Host:** `localhost:3306`  
- **Banco:** `coursejdbc`  
- **Usuário:** `root`  
- **Senha:** *(definida localmente no arquivo DB.java)*

**Tabelas principais:**
- `department(id, name)`
- `seller(id, name, email, birthDate, baseSalary, departmentId)`

---

## 🧠 Exemplo de Execução (Console)

```bash
=== TEST 1: Seller findById ===
Seller [Id: 3, Name: Bob, Email: bob@gmail.com, BaseSalary: 3000.00, Department: Computers]

=== TEST 2: Seller findByDepartment ===
[Seller list by department Computers]

=== TEST 3: Seller findAll ===
[All sellers listed]

=== TEST 4: Seller insert ===
Inserted! New id = 9

=== TEST 5: Seller update ===
Update completed!

=== TEST 6: Seller delete ===
Delete completed!
```

---

### 🧪 Como Executar o Projeto

- 🔧 Pré-requisitos

- ☕ Java 17+

- 🧩 Driver JDBC MySQL (mysql-connector-j.jar)

- 🗄️ Banco MySQL rodando localmente (localhost:3306)

---
### 🚀 Passos

# Clonar o repositório
```
git clone https://github.com/SEU-USUARIO/workshop-jdbc-dao.git
```
```
cd workshop-jdbc-dao
```

# Compilar
```
javac -cp mysql-connector-j.jar application/Program.java
```

# Executar
```
java -cp .;mysql-connector-j.jar application.Program
```
