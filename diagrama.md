```mermaid
graph TD;
    A[Início do Semestre] --> B[Matrícula Online];
    B --> C{Pagamento Confirmado?};
    C -- Sim --> D[Acesso às Aulas];
    C -- Não --> E[Aguardar Validação];
