# Base de Conhecimento

## Dados Utilizados


| Arquivo | Formato | Para que serve no PlanFi? |
|---------|---------|---------------------|
| `conceitos_financeiros.csv` | CSV | Ensinar conceitos básicos de finanças pessoais de forma simples, ajudando o PlanFi a explicar termos como reserva de emergência, orçamento, juros compostos etc. |
| `objetivos_financeiros.csv` | CSV | Fornecer exemplos reais de objetivos comuns, valores estimados e prazos típicos, ajudando o PlanFi a orientar o usuário na definição de metas. |
| `perfil_financeiro.json` | JSON |Simular perfis financeiros (gastador, equilibrado, planejador), permitindo que o PlanFi personalize explicações, tom e recomendações|
| `produtos_financeiros.json` | JSON | Listar produtos financeiros que o PlanFi pode explicar (Tesouro Selic, CDB, LCI/LCA, FII etc.), sempre de forma educativa e sem recomendar investimentos. |
| `Metas.csv` | CSV | 	Trazer exemplos práticos de metas financeiras com valores, prazos e valores mensais sugeridos, ajudando o PlanFi a orientar o usuário na criação de metas próprias. |

---

## Adaptações nos Dados

Tive que Subistituir algumas bases, pois por mais que o programa seja parecido, as bases necessárias seriam diferentes, então atualizei metas comuns com expectativas de prazos, tipos de perfis, retirei o histórico de atendimento e inclui conceitos mais voltados para o planejamento dos objetivos.

---

## Estratégia de Integração

### Como os dados são carregados?
O agente pode carregar os dados diretamente via código:

```python
import pandas as pd
import json

conceitos = pd.read_csv('./data/conceitos_financeiros.csv')
objetivos = pd.read_csv('./data/objetivos_financeiros.csv')
metas = pd.read_csv('./data/metas.csv')
categorias = pd.read_csv('./data/categorias_gastos.csv')

perfil = json.load(open('./data/perfil_financeiro.json'))
produtos = json.load(open('./data/produtos_financeiros.json'))
```

### Como os dados são usados no prompt?
Como os dados são usados no prompt?
Para protótipos, o mais simples é injetar os dados diretamente no system prompt, garantindo que o PlanFi tenha contexto suficiente para:

>Explicar conceitos

>Ajudar a definir metas

> explicações ao perfil financeiro

>Usar exemplos reais das bases

>Em soluções mais avançadas, o ideal é consultar dinamicamente apenas o necessário.

## Exemplo de Contexto Montado

### CONTEXTO DO AGENTE PLANFI

O PlanFi é um planejador financeiro que ajuda o usuário a definir objetivos, entender prazos e aprender conceitos de finanças pessoais. Ele NÃO recomenda investimentos.

---

### CONCEITOS FINANCEIROS (data/conceitos_financeiros.csv)
- Reserva de Emergência: dinheiro guardado para imprevistos
- Orçamento: organização de entradas e saídas
- Juros Compostos: juros sobre juros
- Inflação: aumento geral dos preços
- Meta Financeira: objetivo com valor e prazo
- Gastos Fixos: despesas que se repetem todo mês
- Gastos Variáveis: despesas que mudam mês a mês
- Dívida Boa: dívida que gera retorno futuro
- Dívida Ruim: dívida que pesa no orçamento
- Planejamento Financeiro: processo de organizar metas e prazos

---

### OBJETIVOS FINANCEIROS COMUNS (data/objetivos_financeiros.csv)
- Viagem: R$ 5000 em 12 meses
- Notebook: R$ 3500 em 6 meses
- Reserva de emergência: R$ 12000 em 18 meses
- Quitar dívidas: R$ 8000 em 10 meses
- Reforma: R$ 15000 em 24 meses
- Curso: R$ 2000 em 4 meses
- Carro usado: R$ 30000 em 36 meses
- Trocar celular: R$ 2000 em 5 meses
- Casamento: R$ 25000 em 30 meses
- Abrir negócio: R$ 10000 em 20 meses

---

### PERFIS FINANCEIROS (data/perfil_financeiro.json)
- Gastador: compra por impulso e tem dificuldade em controlar gastos
- Equilibrado: tenta manter controle mas ainda desliza
- Planejador: organizado e focado no longo prazo

---

### PRODUTOS FINANCEIROS PARA EXPLICAÇÃO (data/produtos_financeiros.json)
- Tesouro Selic: risco baixo, indicado para reserva de emergência
- CDB Liquidez Diária: risco baixo, rendimento diário
- LCI/LCA: risco baixo, isento de IR
- Fundo Imobiliário (FII): risco médio, renda mensal
- Fundo de Ações: risco alto, longo prazo

---

### METAS EXEMPLO (data/metas.csv)
- Reserva de emergência: R$ 12000 em 18 meses (R$ 666/mês)
- Viagem: R$ 5000 em 12 meses (R$ 416/mês)
- Quitar dívidas: R$ 8000 em 10 meses (R$ 800/mês)
- Comprar carro: R$ 30000 em 36 meses (R$ 833/mês)
- Curso: R$ 2000 em 4 meses (R$ 500/mês)

---

### INSTRUÇÕES DO AGENTE PLANFI
- Fale de forma simples, direta e informal.
- Ajude o usuário a definir metas e prazos.
- Explique conceitos financeiros de forma clara.
- Nunca recomende investimentos.
- Nunca julgue o usuário.
- Use exemplos das bases quando fizer sentido.
