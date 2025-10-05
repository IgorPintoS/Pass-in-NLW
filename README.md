# Pass.in API

## Visão Geral

O **Pass.in** é uma API RESTful para gestão de participantes em eventos presenciais, desenvolvida em Java com o ecossistema Spring Boot. A aplicação permite que organizadores cadastrem eventos e gerenciem seus participantes, que por sua vez, podem se inscrever e realizar o check-in no dia do evento.

Este projeto demonstra a construção de uma API robusta, seguindo as melhores práticas de desenvolvimento, como arquitetura em camadas, tratamento de exceções, modelagem de dados relacional e automação de migrações de banco de dados.

## Funcionalidades Principais

* **Cadastro de Eventos:** Permite que um organizador cadastre um novo evento, especificando título, detalhes e capacidade máxima de participantes.
* **Consulta de Evento:** Endpoint para visualizar os dados detalhados de um evento, incluindo o número de participantes já inscritos.
* **Inscrição de Participantes:** Permite que um participante se inscreva em um evento (funcionalidade a ser implementada nos controllers).
* **Check-in no Evento:** Endpoint para realizar o check-in de um participante (funcionalidade a ser implementada).
* **Listagem de Participantes:** Endpoint para visualizar a lista de todos os participantes de um determinado evento.

### Regras de Negócio

* O participante só pode se inscrever em um evento uma única vez.
* A inscrição só é permitida em eventos com vagas disponíveis.
* O check-in em um evento é único por participante.

## Arquitetura do Projeto

A aplicação foi desenvolvida utilizando uma arquitetura em camadas bem definida para garantir a separação de responsabilidades e facilitar a manutenção:

* **Controllers:** Expor os endpoints da API REST, tratando as requisições HTTP e as respostas.
* **Services:** Onde se concentra a lógica de negócios da aplicação.
* **Repositories:** Camada de acesso aos dados, utilizando Spring Data JPA para interagir com o banco de dados.
* **Entities:** Classes de domínio que mapeiam as tabelas do banco de dados (`Event`, `Attendee`, `Checkin`).
* **DTOs (Data Transfer Objects):** Utilizados para transportar dados entre as camadas de forma segura e eficiente, evitando a exposição direta das entidades.
* **Exceptions:** Classes de exceção customizadas para um tratamento de erros mais claro e específico.
* **Config:** Camada para configurações globais da aplicação, como o `ControllerAdvice` para manipulação de exceções.

## Tecnologias Utilizadas

* **Java 17**
* **Spring Boot 3.2.4**
* **Spring Data JPA:** Para persistência de dados.
* **Flyway:** Para gerenciamento e versionamento das migrações do banco de dados.
* **HSQLDB:** Banco de dados relacional em memória, ideal para desenvolvimento e testes.
* **Lombok:** Para reduzir o código boilerplate nas classes de domínio e DTOs.
* **Maven:** Para gerenciamento de dependências e do build do projeto.

## Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/igorpintos/pass-in-nlw.git](https://github.com/igorpintos/pass-in-nlw.git)
    ```
2.  **Acesse o diretório do projeto:**
    ```bash
    cd pass-in-nlw
    ```
3.  **Execute o projeto com o Maven:**
    ```bash
    ./mvnw spring-boot:run
    ```
4.  A aplicação estará disponível em `http://localhost:8080`.

## Endpoints da API

* `POST /events`: Cria um novo evento.
* `GET /events/{id}`: Busca os detalhes de um evento específico.
* `GET /events/attendees/{id}`: Retorna a lista de participantes de um evento.
