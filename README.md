```mermaid
flowchart LR
    %% 1. Definição dos Atores (Formas)
    Usu((Usuário))
    Alu((Aluno))
    Pro((Professor))
    Sec((Secretaria))
    Res((Responsável))
    Pag[Sistema de Pagamento]

    %% 2. Hierarquia (Seta de Herança)
    %% Usando a seta simples para evitar erro de leitura no GitHub
    Alu --> Usu
    Pro --> Usu
    Res --> Usu
    Sec --> Usu

    %% 3. Limite do Sistema e Casos de Uso
    subgraph "Sistema de Matrícula Online"
        direction TB
        UC1([Visualizar Cursos])
        UC2([Realizar Matrícula])
        UC3([Ver Notas e Gráficos])
        UC4([Chat de Mensagens])
        UC5([Lançar Notas])
        UC6([Aprovar Matrícula])
    end

    %% 4. Conexões de Interação
    %% O Usuário (Pai) faz as ações comuns
    Usu --- UC1
    Usu --- UC3
    Usu --- UC4

    %% Secretaria e Professor fazem as ações específicas
    Sec --- UC2
    Sec --- UC6
    Pro --- UC5

    %% Sistema Externo
    UC2 --- Pag
