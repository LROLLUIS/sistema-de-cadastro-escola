# sistema-de-cadastro-escola
sistema de cadastro de aluno 
# Sistema de Matrícula Online - Documentação do Projeto

Este projeto visa automatizar o processo de matrícula, acompanhamento acadêmico e comunicação entre os membros de um colégio.

## Diagrama de Casos de Uso

Abaixo está a representação visual das interações dos usuários com o sistema.

```mermaid
useCaseDiagram
    %% Definição dos Atores
    actor "Aluno" as A
    actor "Professor" as P
    actor "Secretaria" as S
    actor "Responsável" as R
    actor "Sist. Pagamento" as SP <<Sistema>>

    package "Sistema de Matrícula Online" {
        usecase "Cadastrar/Login" as UC1
        usecase "Visualizar Cursos" as UC2
        usecase "Realizar Matrícula" as UC3
        usecase "Visualizar Notas e Histórico" as UC4
        usecase "Ver Gráfico de Desempenho" as UC5
        usecase "Trocar Mensagens (Chat)" as UC6
        usecase "Lançar Notas e Frequência" as UC7
        usecase "Disponibilizar Materiais" as UC8
        usecase "Gerenciar Usuários e Cursos" as UC9
        usecase "Aprovar Matrícula" as UC10
        usecase "Processar Pagamento" as UC11
    }

    %% Conexões do Aluno
    A --> UC1
    A --> UC2
    A --> UC3
    A --> UC4
    A --> UC5
    A --> UC6

    %% Conexões do Professor
    P --> UC1
    P --> UC6
    P --> UC7
    P --> UC8

    %% Conexões do Responsável (Pai/Tutor)
    R --> UC1
    R --> UC4
    R --> UC5
    R --> UC6

    %% Conexões da Secretaria
    S --> UC1
    S --> UC6
    S --> UC9
    S --> UC10

    %% Relação entre Casos de Uso e Sistemas Externos
    UC3 ..> UC11 : <<include>>
    UC11 -- SP
