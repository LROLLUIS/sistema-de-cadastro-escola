```mermaid
flowchart LR
    %% 1. Definição dos Atores
    Pessoa((Usuário Geral))
    Alu((Aluno))
    Pro((Professor))
    Sec((Secretaria))
    Pag[Sistema de Pagamento]

    %% 2. Hierarquia (Herança OO)
    Alu --> Pessoa
    Pro --> Pessoa
    Sec --> Pessoa

    %% 3. Limite do Sistema e Casos de Uso Organizados
    subgraph "Sistema de Matrícula Online"
        direction TB
        
        subgraph Modulo_Aluno [Espaço do Aluno]
            UC1([Cadastrar-se])
            UC2([Visualizar Cursos])
            UC3([Matricular-se])
            UC4([Ver Notas e Histórico])
        end

        subgraph Modulo_Professor [Painel do Professor]
            UC5([Acessar Lista de Alunos])
            UC6([Registrar Notas e Frequência])
            UC7([Disponibilizar Materiais])
        end

        subgraph Modulo_Secretaria [Gestão Acadêmica]
            UC8([Gerenciar Alunos/Professores])
            UC9([Criar/Editar Cursos])
            UC10([Aprovar Matrículas])
            UC11([Gerar Relatórios])
        end

        %% Processamento Interno
        UC_Taxa{Processar Taxas}
    end

    %% 4. Conexões de Interação
    %% O Aluno faz suas ações
    Alu --- UC1 & UC2 & UC3 & UC4

    %% O Professor faz suas ações
    Pro --- UC5 & UC6 & UC7

    %% A Secretaria faz suas ações
    Sec --- UC8 & UC9 & UC10 & UC11

    %% Integração com Pagamento (Iniciada pela Matrícula ou Secretaria)
    UC3 -.-> UC_Taxa
    UC10 -.-> UC_Taxa
    UC_Taxa --- Pag
