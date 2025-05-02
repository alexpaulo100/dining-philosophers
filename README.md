# 🍽️ Dining Philosophers Problem  
**Projeto por: Alex Silva**
[![Rust CI](https://github.com/alexpaulo100/dining-philosophers/actions/workflows/ci.yml/badge.svg)](https://github.com/alexpaulo100/dining-philosophers/actions/workflows/ci.yml)
O clássico problema dos **Filósofos Jantando**, implementado com segurança de concorrência usando **Rust**.  
Este projeto demonstra técnicas modernas para evitar *deadlock* ao acessar recursos compartilhados entre múltiplas threads.

---

## 📝 Descrição

O problema dos Filósofos Jantando é um exemplo clássico da ciência da computação para ilustrar os desafios de:
- Concorrência entre threads
- Deadlocks
- Controle de acesso a recursos compartilhados (locks)

Neste projeto:
- Os **filósofos** são modelados como *threads*.
- Os **garfos** são modelados como `Mutex<()>`, protegendo o acesso exclusivo.
- Os `Arc` permitem compartilhar os garfos de forma segura entre múltiplas threads com contagem de referência.

### ✅ Estratégias para Evitar Deadlock:
- Cada filósofo sempre adquire **primeiro o garfo com o menor número**, quebrando a simetria que poderia levar a espera circular (*deadlock*).
- Utilizamos o rigor do compilador Rust para garantir segurança em tempo de compilação.

---

## 🚀 Como Funciona

- Cria **15 filósofos** e **4 garfos**.
- Cada filósofo tenta comer pegando os dois garfos mais próximos (com bloqueio Mutex).
- A simulação imprime:
  - Quando cada filósofo pega os garfos.
  - O momento que começam a comer.
  - E quando terminam a refeição.
  - O tempo total de execução.

### 🔑 Técnicas Utilizadas
- `Mutex<()>` para garantir acesso exclusivo aos garfos.
- `Arc` para compartilhar garfos entre threads de forma segura.
- Aquisição ordenada dos garfos (menor número primeiro) para evitar deadlock.
- Medição de tempo com `Instant` para análise da performance.

---

## 📦 Tecnologias

- **Linguagem:** Rust 🦀
- **Thread Safety:** `Arc`, `Mutex`
- **Concorrência:** `std::thread`
- **Tempo:** `std::time::Instant`

---

## ▶️ Como Executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/alexpaulo100/dining-philosophers.git
   cd dining-philosophers
