```mermaid
flowchart TD
    %% Herança de Atores (Conceito OO)
    Usuario((Usuário Autenticado))
    
    Aluno((Aluno)) --|> Usuario
    Prof((Professor)) --|> Usuario
    Resp((Responsável)) --|> Usuario
    Sec((Secretaria)) --|> Usuario

    %% Sistema Externo
    Pag[<< Interface >>\nSistema de Pagamento]

    subgraph "Sistema de Matrícula Online"
        %% Casos de Uso Comuns
        UC_Base([Login / Logout])
        UC_Chat([Trocar Mensagens])

        %% Casos de Uso Específicos
        subgraph "Módulo Acadêmico"
            UC4([Visualizar Notas])
            UC5([Gráfico de Desempenho])
            UC7([Lançar Notas/Frequência])
            UC8([Upload Materiais])
        end

        subgraph "Módulo Administrativo"
            UC3([Realizar Matrícula])
            UC9([Gerenciar Cadastros])
            UC10([Aprovar Matrícula])
            UC11{Processar Taxa}
        end
    end

    %% Relacionamentos de Generalização (Linhas que saem do Usuário)
    Usuario --- UC_Base
    Usuario --- UC_Chat

    %% Relacionamentos de Especialização
    Aluno --- UC3 & UC4 & UC5
    Resp --- UC4 & UC5
    Prof --- UC7 & UC8
    Sec --- UC9 & UC10

    %% Relacionamentos de Dependência (OO)
    UC3 -.->|<< include >>| UC11
    UC11 --- Pag
