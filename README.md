# About the Project

This project for a fictitious retail store. I modeled the Relational Database and the Datawarehouse, going through the data loading phase with the ETL tool, Integration Services, after that I created the cubes in Analysis Services and finally, I analyzed the information with Report Services, the Microsoft Reporting tool. 
I joined the knowledge of Microsoft's Excel tools in a "real" project. The data will be fictitious and the DW created will be from the point of view of sales.


## Layout mobile
![Mobile 1](https://github.com/acenelio/assets/raw/main/sds1/mobile1.png) ![Mobile 2](https://github.com/acenelio/assets/raw/main/sds1/mobile2.png)

## Layout web
![Web 1](https://github.com/acenelio/assets/raw/main/sds1/web1.png)

![Web 2](https://github.com/acenelio/assets/raw/main/sds1/web2.png)

## Modelo conceitual
![Modelo Conceitual](https://github.com/acenelio/assets/raw/main/sds1/modelo-conceitual.png)

# Tecnologias utilizadas
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


# Como executar o projeto

## Back end
Pré-requisitos: Java 11

```bash
# clonar repositório
git clone https://github.com/devsuperior/sds1-wmazoni

# entrar na pasta do projeto back end
cd backend

# executar o projeto
./mvnw spring-boot:run
```

## Front end web
Pré-requisitos: npm / yarn

```bash
# clonar repositório
git clone https://github.com/devsuperior/sds1-wmazoni

# entrar na pasta do projeto front end web
cd front-web

# instalar dependências
yarn install

# executar o projeto
yarn start
```

# Autor

Wellington Mazoni de Andrade

https://www.linkedin.com/in/wmazoni
