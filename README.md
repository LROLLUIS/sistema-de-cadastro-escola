```mermaid
flowchart TD
    %% Definição de Atores (Herança OO)
    Usuario((Usuário Autenticado))
    
    Aluno((Aluno)) --> Usuario
    Prof((Professor)) --> Usuario
    Resp((Responsável)) --> Usuario
    Sec((Secretaria)) --> Usuario

    %% Sistema Externo
    Pag[<< Interface >> Sistema de Pagamento]

    subgraph Sistema_Escolar [Sistema de Matrícula Online]
        direction TB
        
        %% Módulos como Pacotes de Objetos
        subgraph Modulo_Comum [Base / Comum]
            UC1([Login / Logout])
            UC6([Chat / Mensagens])
        end

        subgraph Modulo_Academico [Acadêmico]
            UC4([Visualizar Notas])
            UC5([Gráfico de Desempenho])
            UC7([Lançar Notas/Frequência])
            UC8([Upload Materiais])
        end

        subgraph Modulo_Adm [Administrativo]
            UC3([Realizar Matrícula])
            UC9([Gerenciar Cadastros])
            UC10([Aprovar Matrícula])
            UC11{Processar Taxa}
        end
    end

    %% Relacionamentos herdados do Usuário
    Usuario --- UC1
    Usuario --- UC6

    %% Relacionamentos específicos (Polimorfismo de acesso)
    Aluno --- UC3 & UC4 & UC5
    Resp --- UC4 & UC5
    Prof --- UC7 & UC8
    Sec --- UC9 & UC10

    %% Dependência de Matrícula
    UC3 -.->|include| UC11
    UC11 --- Pag
