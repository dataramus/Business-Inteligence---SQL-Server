# Business Inteligence with SQL Server
[![NPM](https://img.shields.io/npm/l/react)]([https://github.com/devsuperior/sds1-wmazoni/blob/master/LICENSE](https://github.com/dataramus/Business-Inteligence---SQL-Server/commit/497960fa002cf5cfc023530f1d8c5d7b54c986e3)) 

# About the Project

This project for a fictitious retail store. I modeled the Relational Database and the Datawarehouse, going through the data loading phase with the ETL tool, Integration Services, after that I created the cubes in Analysis Services and finally, I analyzed the information with Report Services, the Microsoft Reporting tool. 
I joined the knowledge of Microsoft's Excel tools in a project. The data will be fictitious and the DW created will be from the point of view of sales.

![logic model](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Image/ETL%20and%20cubes.png)

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
	.
	.
	.	
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

### Interview with Managers
You can see all the interview at https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Tera%20Requirements%20Document.pdf
![entrevista](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Image/entrevista.png)

### Change of Requirements
![requisitos](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Image/mudanca%20requisitos.png)

### Logic Modeling
https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/02%20-%20STAGE.mdj
![logic model](https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/DATABASE%20DIAGRAM.png)

### Phisical Modeling
13 - Create Stage Area: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/13%20-%20CREATION%20OF%20THE%20STAGE%20AREA.sql
```sql
CREATE DATABASE COMERCIO_STAGE
GO

USE COMERCIO_STAGE
GO

CREATE TABLE ST_CLIENTE(
	IDCLIENTE INT DEFAULT NULL,
	NOME VARCHAR(100) DEFAULT NULL,
	SEXO VARCHAR(20) DEFAULT NULL,
	NASCIMENTO DATE DEFAULT NULL,
	CIDADE VARCHAR(100) DEFAULT NULL,
	ESTADO VARCHAR(10) DEFAULT NULL,
	REGIAO VARCHAR(20) DEFAULT NULL
)
GO
	.
	.
	.	
```
### ETL - Integration Services
Now inside the Visual Studio (https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/PROJETO_BI/PROJETO_BI.sln) I created a connection between OLTP and Stage using the SISS Package.
After created I Load the from OLTP area to Stage area, that you can see at the file PROK_ETL (https://github.com/dataramus/Business-Inteligence---SQL-Server/tree/main/PROJETO_BI/PROJ_ETL)

14 - Products table in Camel Case: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/14%20-%20CAMEL%20CASE%20CURSOR.sql

15 - Sales Report (for the Nota Fiscal): https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/15%20-%20LOAD%20VIEW%20SALLES%20REPORT.sql

## DATAWAREHOUSE (DW)
### Logic Modeling
https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/modeling/03%20-%20DATAWAREHOUSE.mdj

### Phisical Modeling
16 - Create DW: https://github.com/dataramus/Business-Inteligence---SQL-Server/blob/main/Scripts%20PT/16%20-%20DATA%20WAREHOUSE.sql

Luis Coelho

https://www.linkedin.com/in/luis-coelho-913093116/
