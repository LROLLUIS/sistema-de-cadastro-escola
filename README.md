```mermaid
flowchart LR
    %% Atores
    Aluno((Aluno))
    Prof((Professor))
    Sec((Secretaria))
    Resp((Responsável))
    Pag[Sistema de Pagamento]

    subgraph "Sistema de Matrícula Online"
        UC1([Cadastrar/Login])
        UC2([Visualizar Cursos])
        UC3([Realizar Matrícula])
        UC4([Visualizar Notas])
        UC5([Gráfico de Desempenho])
        UC6([Chat/Mensagens])
        UC7([Lançar Notas/Frequência])
        UC8([Materiais Didáticos])
        UC9([Gerenciar Usuários])
        UC10([Aprovar Matrícula])
        UC11([Processar Pagamento])
    end

    %% Conexões Aluno
    Aluno --- UC1
    Aluno --- UC2
    Aluno --- UC3
    Aluno --- UC4
    Aluno --- UC5
    Aluno --- UC6

    %% Conexões Professor
    Prof --- UC1
    Prof --- UC6
    Prof --- UC7
    Prof --- UC8

    %% Conexões Responsável
    Resp --- UC1
    Resp --- UC4
    Resp --- UC5
    Resp --- UC6

    %% Conexões Secretaria
    Sec --- UC1
    Sec --- UC6
    Sec --- UC9
    Sec --- UC10

    %% Integração Pagamento
    UC3 -.-> UC11
    UC11 --- Pag
