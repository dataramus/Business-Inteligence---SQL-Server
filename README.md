# Big Game Survey 
[![NPM](https://img.shields.io/npm/l/react)]([https://github.com/devsuperior/sds1-wmazoni/blob/master/LICENSE](https://github.com/dataramus/Business-Inteligence---SQL-Server/commit/497960fa002cf5cfc023530f1d8c5d7b54c986e3)) 

# About the Project

This project for a fictitious retail store. I modeled the Relational Database and the Datawarehouse, going through the data loading phase with the ETL tool, Integration Services, after that I created the cubes in Analysis Services and finally, I analyzed the information with Report Services, the Microsoft Reporting tool. 
I joined the knowledge of Microsoft's Excel tools in a project. The data will be fictitious and the DW created will be from the point of view of sales.


# Project Steps
- Installation of the environment
- Creating the Relational Database
- Relational Database Modeling
- Generation of fictitious data in relational database, with TSQL techniques
- Creation of the stage area
- Data loading from the operational to the stage area, using Integration Services
- Creation of the Datawarehouse
- Datawarehouse Modeling
- INCREMENTAL Data Load from Stage Dimensions to the Datawarehouse, using Integration Services with SCD techniques.
- Loading the Fact Table from the Stage to the DW, using TSQL programming with Integration Services and the Watermark technique
- Cube Assembly in Analysis Services
- Analysis in Excel, with creation of Dashboards
- Creating Reports in the OLTP environment and in the OLAP environment


# How to do the Project

##      OLTP

### Logic Modeling
  https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/01%20-%20OLTP.mdj
![logic model](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/entity%20relationship%20diagram%20(ERP).jpg)

### Phisical Modeling
1 - Creating Tables  https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/01%20-%20OLTP%20TRANDING%20MODELING.sql
```sql
/* OLTP TRADE MODELING */

CREATE DATABASE COMERCIO_OLTP
GO

USE COMERCIO_OLTP
GO

CREATE TABLE CLIENTE(
	IDCLIENTE INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(30) NOT NULL,
	SOBRENOME VARCHAR(30) NOT NULL,
	EMAIL VARCHAR(60) NOT NULL,
	SEXO CHAR(1) NOT NULL,
	NASCIMENTO DATE NOT NULL
)	
GO

CREATE TABLE ENDERECO(
	IDENDERECO INT PRIMARY KEY IDENTITY,
	RUA VARCHAR(100) NOT NULL,
	CIDADE VARCHAR(50) NOT NULL,
	ESTADO VARCHAR(20) NOT NULL,
	REGIAO VARCHAR(20) NOT NULL,
	ID_CLIENTE INT UNIQUE
)
GO

CREATE TABLE VENDEDOR(
	IDVENDEDOR INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(30) NOT NULL,
	SEXO CHAR(1) NOT NULL,
	EMAIL VARCHAR(30) NOT NULL,
	ID_GERENTE INT
)
GO

CREATE TABLE CATEGORIA(
	IDCATEGORIA INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(30) NOT NULL
)
GO

CREATE TABLE FORNECEDOR(
	IDFORNECEDOR INT PRIMARY KEY IDENTITY,
	NOME VARCHAR(50) NOT NULL
)
GO

CREATE TABLE PRODUTO(
	IDPRODUTO INT PRIMARY KEY IDENTITY,
	PRODUTO VARCHAR(100) NOT NULL,
	VALOR NUMERIC(10,2) NOT NULL,
	CUSTO_MEDIO NUMERIC(10,2),
	ID_CATEGORIA INT,
	ID_FORNECEDOR INT
)
GO

CREATE TABLE FORMA_PAGAMENTO(
	IDFORMA INT PRIMARY KEY IDENTITY,
	FORMA VARCHAR(40) NOT NULL
)
GO

CREATE TABLE ITEM_NOTA(
	IDITEMNOTA INT PRIMARY KEY IDENTITY,
	ID_PRODUTO INT,
	ID_NOTA_FISCAL INT,
	QUANTIDADE INT,
	TOTAL NUMERIC(10,2)	
)
GO

CREATE TABLE NOTA_FISCAL(
	IDNOTA INT PRIMARY KEY IDENTITY(1000,10),
	DATA DATE,
	TOTAL NUMERIC(10,2),
	ID_FORMA INT,
	ID_CLIENTE INT,
	ID_VENDEDOR INT
)
GO
```

### Load Tables

Run the SQL codes below to load the tables


2 - Load Cliente: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/02%20-%20LOAD%20CLIENTES.sql

3 - Load Endereco: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/03%20-%20LOAD%20ENDERECO.sql (This one I imported data from Excel{https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/03%20-%20LOAD%20ADDRESS.xls})

4 - Load Categoria: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/04%20-%20LOAD%20CATEGORIA.sql

5 - Load Fornecedor: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/05%20-%20LOAD%20FORNECEDOR.sql

6 - Load Produto: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/06%20-%20LOAD%20PRODUTO.sql

7 - Load Vendedor: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/07%20-%20LOAD%20VENDEDOR.sql

8 - Load Pagamento: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/08%20-%20LOAD%20PAGAMENTO(PAYMENT)%20METHOD.sql

9 - Completing NF: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/09%20-%20COMPLETING%20THE%20NOTA_FISCAL%20TABLE.sql

10 - Load Item Nota: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/10%20-%20LOAD%20ITEM%20NOTA.sql

11 - Nota Update: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/11%20-%20NOTA(INVOICE)%20UPDATE.sql

12 - Enabling Restrictions: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/12%20-%20ENABLING%20RESTRICTIONS.sql

## STAGE

### Logic Modeling
https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/02%20-%20STAGE.mdj
![logic model](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/DATABASE%20DIAGRAM.png)



# Autor

Luis Coelho

https://www.linkedin.com/in/luis-coelho-913093116/
