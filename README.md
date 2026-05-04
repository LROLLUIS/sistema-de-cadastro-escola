```mermaid
flowchart TD
    %% Atores no Topo
    Aluno((Aluno))
    Resp((Responsável))
    Prof((Professor))
    Sec((Secretaria))

    subgraph "Sistema de Matrícula Online"
        direction TB
        
        %% Grupo de Acesso e Comunicação
        subgraph "Base"
            UC1([Cadastrar/Login])
            UC6([Chat/Mensagens])
        end

        %% Grupo Acadêmico
        subgraph "Acadêmico"
            UC4([Visualizar Notas])
            UC5([Gráfico de Desempenho])
            UC7([Lançar Notas/Frequência])
            UC8([Materiais Didáticos])
        end

        %% Grupo Administrativo
        subgraph "Administrativo"
            UC2([Visualizar Cursos])
            UC3([Realizar Matrícula])
            UC10([Aprovar Matrícula])
            UC9([Gerenciar Usuários])
            UC11([Processar Pagamento])
        end
    end

    %% Sistema Externo na Lateral
    Pag[Sistema de Pagamento]

    %% Conexões Aluno
    Aluno --- UC1 & UC2 & UC3 & UC4 & UC5 & UC6

    %% Conexões Responsável
    Resp --- UC1 & UC4 & UC5 & UC6

    %% Conexões Professor
    Prof --- UC1 & UC6 & UC7 & UC8

    %% Conexões Secretaria
    Sec --- UC1 & UC6 & UC9 & UC10

    %% Integração Pagamento
    UC3 -.-> UC11
    UC11 --- Pag
