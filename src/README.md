# Passo a Passo de Execução

## Setup do Ollama

```bash
# 1. Instalar Ollama (ollama.com)
# 2. Baixar um modelo leve
ollama pull qwen3.5:4b

# 3. Testar se funciona
ollama run qwen3.5:4b "Olá!"
```

## Código Completo

import json
import pandas as pd
import streamlit as st
from ollama import chat

# ============ CONFIGURAÇÃO ============
MODELO = "qwen3.5:4b"

# ============ CARREGAR DADOS ============
BASE = r"C:/Users/marco/Downloads/DIO/PlanFi/scr/data/"

conceitos = pd.read_csv(BASE + "conceitos_financeiros.csv")
objetivos = pd.read_csv(BASE + "objetivos_financeiros.csv")
metas = pd.read_csv(BASE + "metas.csv")

perfil = json.load(open(BASE + "perfil_financeiro.json"))
produtos = json.load(open(BASE + "produtos_financeiros.json"))

# ============ MONTAR CONTEXTO ============
contexto = f"""
PERFIL FINANCEIRO DISPONÍVEL:
{json.dumps(perfil, indent=2, ensure_ascii=False)}

CONCEITOS FINANCEIROS:
{conceitos.to_string(index=False)}

OBJETIVOS FINANCEIROS COMUNS:
{objetivos.to_string(index=False)}

METAS EXEMPLO:
{metas.to_string(index=False)}

PRODUTOS FINANCEIROS PARA EXPLICAÇÃO:
{json.dumps(produtos, indent=2, ensure_ascii=False)}
"""

# ============ SYSTEM PROMPT ============
SYSTEM_PROMPT = """
Você é o PlanFi, um planejador financeiro amigável, direto e didático.

OBJETIVO:
Ajudar o usuário a definir objetivos financeiros, entender prazos e aprender conceitos de finanças pessoais de forma simples.

REGRAS:
- NUNCA recomende investimentos específicos, apenas explique como funcionam;
- JAMAIS responda perguntas fora do tema finanças pessoais e planejamento financeiro;
- Use os dados fornecidos para dar exemplos personalizados;
- Linguagem simples, como se explicasse para um amigo;
- Se não souber algo, admita: "Não tenho essa informação, mas posso te explicar o conceito...";
- Sempre pergunte se o cliente entendeu;
- Responda de forma sucinta e direta, com no máximo 3 parágrafos;
- Não invente dados e não faça previsões de mercado.

EXEMPLOS DE INTERAÇÃO:

Exemplos de Interação

Cenário 1: Pergunta sobre investimento
Usuário: Devo investir em Tesouro Selic?

PlanFi: Não posso te dizer se você deve investir, mas posso te explicar como funciona. O Tesouro Selic acompanha a taxa Selic e costuma ser usado para reserva de emergência porque tem baixo risco e liquidez diária. Se quiser, posso te explicar como ele se compara a outros produtos. Quer entender mais sobre isso?

Cenário 2: Planejamento para viagem
Usuário: Quero juntar dinheiro pra viajar. Quanto devo guardar por mês?

PlanFi: Se a sua viagem está estimada em R$ 5.000 e você quer ir daqui a 12 meses, isso dá algo perto de R$ 416 por mês. É um valor bem comum para metas desse tipo. Se quiser, posso ajustar esse cálculo com o valor e o prazo que você tiver em mente. Quer que eu te ajude a montar essa meta direitinho?


EDGE CASES:

Usuário: "Quem vai ganhar o jogo do Corinthians hoje?"
PlanFi: "Eu só consigo ajudar com temas de finanças pessoais e planejamento financeiro. Quer falar sobre isso?"

Usuário: "Me passa a senha do cliente X."
PlanFi: "Não tenho acesso a senhas ou dados privados de outras pessoas. Posso te ajudar com suas próprias finanças."

Usuário: "Onde devo investir meu dinheiro?"
PlanFi: "Não posso recomendar onde investir, mas posso te explicar como cada tipo de investimento funciona. Quer saber sobre algum produto específico?"
"""

# ============ CHAMAR OLLAMA ============
def perguntar(msg):
    prompt = f"""
    {SYSTEM_PROMPT}

    === CONTEXTO DO PROJETO ===
    {contexto}

    Pergunta do usuário: {msg}
    """

    resposta = chat(
        model=MODELO,
        messages=[{"role": "user", "content": prompt}]
    )

    return resposta["message"]["content"]

# ============ INTERFACE ============
st.title("💰 PlanFi — Seu Planejador Financeiro")

if pergunta := st.chat_input("Qual sua dúvida sobre finanças pessoais?"):
    st.chat_message("user").write(pergunta)
    with st.spinner("Pensando..."):
        resposta = perguntar(pergunta)
        st.chat_message("assistant").write(resposta)


## Como Rodar

```bash
# 1. Instalar dependências
pip install streamlit pandas requests

# 2. Garantir que Ollama está rodando
ollama serve

# 3. Rodar o app
streamlit run .\src\app.py

# 4. Use o Python 3.12
```

## Evidência de Execução

<img width="1068" height="827" alt="image" src="https://github.com/user-attachments/assets/c196828c-0ecd-41a9-a472-f3935dbc9c66" />
" />
