#Pass.in
O pass.in é uma aplicação de gestão de participantes em eventos presenciais.

A ferramenta permite que o organizador cadastre um evento e abra uma página pública de inscrição.

Os participantes inscritos podem emitir uma credencial para check-in no dia do evento.

O sistema fará um scan da credencial do participante para permitir a entrada no evento.

##Requisitos
###Requisitos funcionais
 O organizador deve poder cadastrar um novo evento;
 O organizador deve poder visualizar dados de um evento;
 O organizador deve poser visualizar a lista de participantes;
 O participante deve poder se inscrever em um evento;
 O participante deve poder visualizar seu crachá de inscrição;
 O participante deve poder realizar check-in no evento;
 
###Regras de negócio
 O participante só pode se inscrever em um evento uma única vez;
 O participante só pode se inscrever em eventos com vagas disponíveis;
 O participante só pode realizar check-in em um evento uma única vez;
 
##Diagrama do banco de dados
erDiagram
    events ||--o{ attendees : "1-N"
    attendees ||--o| check_ins : "1-1 (unique)"

    events {
        TEXT id PK "Identificador único"
        TEXT title "Título do evento"
        TEXT details "Detalhes (opcional)"
        TEXT slug UK "Slug único"
        INTEGER maximum_attendees "Máximo de participantes"
    }
    
    attendees {
        INTEGER id PK "ID autoincrement"
        TEXT name "Nome do participante"
        TEXT email "E-mail"
        TEXT event_id FK "Chave estrangeira para events"
        DATETIME created_at "Data de criação"
    }
    
    check_ins {
        INTEGER id PK "ID autoincrement"
        DATETIME created_at "Data do check-in"
        INTEGER attendeeId FK,UK "Chave estrangeira única para attendees"
    }
