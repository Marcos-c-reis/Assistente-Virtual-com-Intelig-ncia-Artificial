# Avaliação e Métricas

## Como Avaliar seu Agente

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar o perfil financeiro e receber o perfil correto |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Recomendar produto compatível com o perfil financeiro |


---

## Exemplos de Cenários de Teste

### Teste 1: Consulta de gastos
- **Pergunta:** "Qual é o meu perfil financeiro?"
- **Resposta esperada:** O PlanFi deve identificar corretamente um dos perfis do arquivo perfil_financeiro.json (Gastador, Equilibrado ou Planejador).
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2: Recomendação de produto
- **Pergunta:** Qual investimento você recomenda para alguém com perfil conservador?"
- **Resposta esperada:** Um produto de renda fixa e risco baixo, como:
>Tesouro Selic
>CDB Liquidez Diária
>LCI/LCA
(dados de produtos_financeiros.json)

- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual é o valor estimado para fazer uma viagem?"
- **Resposta esperada:** R$ 5.000,00
(dado do arquivo objetivos_financeiros.csv)
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Quem ganhou o campeonato brasileiro?"
- **Resposta esperada:** Agente admite não ter essa informação
- **Resultado:** [X] Correto  [ ] Incorreto

---

## Formulário de Feedback (Sugestão)


| Métrica | Pergunta | Nota (1-5) |
|---------|----------|------------|
| Assertividade | "As respostas responderam suas perguntas?" | 3 |
| Segurança | "As informações pareceram confiáveis?" | 4 |
| Coerência | "A linguagem foi clara e fácil de entender?" | 3 |

**Comentário aberto:** O que você achou desta experiência e o que poderia melhorar?


Acho que com uma base maior de dados de movimentação e objetivos, talvez troucesse respostas mais acertivas


## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Questões técnicas respondidas com exatidão;
- Cordialidade nas respostas;
- Sem julgamentos sobre a condição atual do cliente;

**O que pode melhorar:**
- Por rodar local, o tempo de resposta foi muito elevado;
- Respostas ainda muito genéricas principalmente quando questões personalizadas;

