<div align="center">

# 💰 PlanFi

### Seu Planejador Financeiro com Inteligência Artificial

*Planeje, aprenda e evolua com o poder da IA generativa local*

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-Local_LLM-black?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Concluído-28a745?style=for-the-badge)

</div>

---

## 📌 Sobre o Projeto

O **PlanFi** é um assistente de planejamento financeiro pessoal com IA generativa que roda **100% localmente**, sem enviar seus dados para serviços externos. Ele conversa com o usuário para ajudá-lo a definir objetivos financeiros, entender prazos e aprender conceitos de finanças de forma simples, personalizada e segura.

O assistente adapta suas respostas ao **perfil financeiro do usuário** — Gastador, Equilibrado ou Planejador — e usa uma base de conhecimento estruturada com conceitos, metas, objetivos e produtos financeiros reais.

> 🎓 Projeto desenvolvido como entrega final do **Bradesco - GenAI & Dados** na [DIO](https://www.dio.me/).

---

## ✨ Funcionalidades

- 💬 **Chat conversacional** com IA para tirar dúvidas financeiras
- 🎯 **Definição e cálculo de metas** (viagem, reserva de emergência, aposentadoria, etc.)
- 👤 **Perfil financeiro personalizado** com base no comportamento do usuário
- 📚 **Educação financeira** com explicações simples sobre produtos e conceitos
- 🔒 **Privacidade total** — roda localmente com Ollama, sem enviar dados a APIs externas
- 🚫 **Anti-alucinação** — não inventa dados, não faz previsões de mercado

---

## 🚫 Limitações (por design)

O PlanFi foi construído com limites intencionais para garantir segurança e conformidade:

| O PlanFi **faz** | O PlanFi **não faz** |
|---|---|
| Explica como produtos financeiros funcionam | Recomenda onde investir |
| Ajuda a calcular metas financeiras | Acessa dados bancários reais |
| Adapta exemplos ao perfil do usuário | Responde perguntas fora de finanças |
| Admite quando não tem informação | Inventa dados ou faz previsões |

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| [Python 3.10+](https://www.python.org/) | Linguagem principal |
| [Streamlit](https://streamlit.io/) | Interface web conversacional |
| [Ollama](https://ollama.com/) | Execução local do modelo de linguagem |
| `qwen3.5:4b` | Modelo LLM utilizado |
| `pandas` | Leitura e manipulação dos dados CSV |
| JSON / CSV | Base de conhecimento estruturada |

---

## 📁 Estrutura do Projeto

```
PlanFi/
├── scr/
│   ├── App.py                             # Aplicação principal (Streamlit + Ollama)
│   └── data/
│       ├── perfil_financeiro.json         # Perfis: Gastador, Equilibrado, Planejador
│       ├── produtos_financeiros.json      # Produtos financeiros (Tesouro, CDB, FII, etc.)
│       ├── conceitos_financeiros.csv      # Base de conceitos financeiros
│       ├── objetivos_financeiros.csv      # Objetivos financeiros comuns
│       └── metas.csv                      # Exemplos de metas financeiras
└── README.md
```

---

## 🚀 Como Executar

### Pré-requisitos

- Python 3.10 ou superior
- [Ollama](https://ollama.com/) instalado na máquina

### 1. Instalar e iniciar o Ollama

```bash
# Baixe o Ollama em: https://ollama.com
ollama pull qwen3:5b
ollama serve
```

### 2. Clonar o repositório

```bash
git clone https://github.com/Marcos-c-reis/Assistente-Virtual-com-Intelig-ncia-Artificial.git
cd Assistente-Virtual-com-Intelig-ncia-Artificial
```

### 3. Instalar as dependências

```bash
pip install streamlit pandas ollama
```

### 4. Rodar a aplicação

```bash
streamlit run scr/App.py
```

Acesse no navegador: [http://localhost:8501](http://localhost:8501)

---

## 💬 Exemplos de Uso

**Planejamento de meta:**
> 👤 "Quero juntar dinheiro pra viajar. Quanto devo guardar por mês?"
>
> 🤖 "Se a sua viagem está estimada em R$ 5.000 e você quer ir daqui a 12 meses, isso dá algo perto de R$ 416 por mês. Se quiser, posso ajustar esse cálculo com o valor e o prazo que você tiver em mente. Quer que eu te ajude a montar essa meta?"

---

**Dúvida sobre investimento:**
> 👤 "O que é Tesouro Selic?"
>
> 🤖 "O Tesouro Selic acompanha a taxa básica de juros da economia e é considerado um dos investimentos mais seguros do Brasil. Ele tem liquidez diária, ou seja, você pode resgatar quando precisar. Por isso é muito usado como reserva de emergência. Quer saber como ele se compara ao CDB?"

---

**Fora do escopo:**
> 👤 "Quem vai ganhar o jogo do Corinthians hoje?"
>
> 🤖 "Eu só consigo ajudar com temas de finanças pessoais e planejamento financeiro. Quer falar sobre isso?"

---

## 👤 Perfis Financeiros

O PlanFi identifica e adapta suas respostas a três perfis:

| Perfil | Características | Principais Desafios |
|---|---|---|
| 🔴 **Gastador** | Compra por impulso, foco no curto prazo, dificuldade em manter metas | Criar hábitos de organização, construir reserva de emergência |
| 🟡 **Equilibrado** | Controla parte dos gastos, tem metas mas nem sempre acompanha | Criar consistência no planejamento, evitar deslizes mensais |
| 🟢 **Planejador** | Acompanha orçamento, define metas claras, pensa no longo prazo | Evitar rigidez excessiva, atualizar metas conforme mudanças de vida |

---

## 📊 Base de Conhecimento

O PlanFi utiliza dados estruturados para contextualizar as respostas:

- **Produtos financeiros:** Tesouro Selic, CDB Liquidez Diária, LCI/LCA, FII, Fundo de Ações
- **Conceitos financeiros:** definições e explicações didáticas
- **Objetivos comuns:** viagem, aposentadoria, imóvel, reserva de emergência
- **Metas exemplo:** valores, prazos e estratégias de aporte

---

## 🏗️ Arquitetura

```
Usuário
   │
   ▼
Streamlit (Interface Web)
   │
   ▼
System Prompt + Contexto (perfil, metas, produtos, conceitos)
   │
   ▼
Ollama — qwen3.5:4b (LLM local)
   │
   ▼
Resposta educativa personalizada
```

---

## 🔒 Privacidade e Segurança

- **Nenhum dado é enviado para servidores externos** — o modelo roda localmente via Ollama
- O assistente **não acessa** contas bancárias, CPF ou dados sensíveis
- Todas as informações são **mockadas** — o projeto usa dados fictícios para fins educacionais

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

1. Faça um fork do projeto
2. Crie uma branch: `git checkout -b minha-feature`
3. Commit suas mudanças: `git commit -m 'feat: minha feature'`
4. Push para a branch: `git push origin minha-feature`
5. Abra um Pull Request

---
