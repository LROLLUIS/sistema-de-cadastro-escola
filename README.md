```mermaid
flowchart TD
    %% Atores (Círculos)
    Aluno((Aluno))
    Resp((Responsável))
    Prof((Professor))
    Sec((Secretaria))

    %% Sistema Externo (Quadrado)
    Pag[Sistema de Pagamento]

    subgraph "Sistema de Matrícula Online"
        direction TB
        
        %% Casos de Uso (Cápsulas/Elipses)
        Login([Login/Autenticação])
        Chat([Chat de Comunicação])
        Matricula([Realizar Matrícula])
        Notas([Ver Notas/Boletim])
        Grafico([Gráfico de Desempenho])
        Lancar([Lançar Notas/Frequência])
        Materiais([Upload de Materiais])
        Gestao([Gerenciar Usuários/Cursos])
        
        %% Ponto de Decisão (Losango)
        Aprovacao{Aprovar Matrícula?}
        CheckPag{Pagamento OK?}
    end

    %% Fluxo do Aluno
    Aluno --- Login
    Login --- Chat
    Aluno --- Matricula
    Matricula --> CheckPag
    CheckPag -- Sim --> Notas
    Aluno --- Grafico

    %% Fluxo do Responsável
    Resp --- Login
    Resp --- Notas
    Resp --- Grafico
    Resp --- Chat

    %% Fluxo do Professor
    Prof --- Login
    Prof --- Lancar
    Prof --- Materiais
    Prof --- Chat

    %% Fluxo da Secretaria
    Sec --- Login
    Sec --- Gestao
    Sec --- Aprovacao
    Aprovacao -- Sim --> Matricula
    Sec --- Chat

    %% Integração com Sistema Externo
    CheckPag -- Não --> Pag
    Pag -- Confirmação --> CheckPag
