# 🐞 Bug Tracker – Sistema de Rastreamento de Bugs  

**Autor:** Heverton Silva de Souza  
**Disciplina:** Desenvolvimento Web  
**Instituição:** Instituto Federal Fluminense

---

## 📘 Descrição Geral

O **Bug Tracker** é uma ferramenta corporativa voltada para equipes de desenvolvimento de software que desejam **reportar, atribuir e acompanhar o status de bugs e tarefas internas** (chamados) dentro de diferentes projetos.  

O sistema busca centralizar o fluxo de comunicação entre **Desenvolvedores**, **QAs** e **Gerentes de Projeto**, garantindo rastreabilidade e controle de mudanças durante o ciclo de vida de cada bug.

---

## 👥 Perfis de Usuário

| Perfil | Permissões Principais |
|--------|------------------------|
| 🧑‍💼 **Gerente de Projeto (Admin)** | Cria projetos, adiciona membros e atribui chamados a desenvolvedores. |
| 👨‍💻 **Desenvolvedor (Membro)** | Visualiza e atualiza chamados atribuídos. Pode comentar e alterar status quando permitido. |
| 🧪 **QA / Testador (Reportador)** | Cria chamados, adiciona anexos e verifica correções. |

---

## 🧩 Lógica de Negócio Principal

- O **Gerente** cria um **Projeto** e adiciona **Desenvolvedores** (relação *ManyToMany* entre `Usuário` e `Projeto`).
- Qualquer **membro** pode criar um **Chamado (Bug)** e associá-lo a um projeto.
- O **Gerente** pode **atribuir** o chamado a um **Desenvolvedor específico** do projeto.
- O sistema gerencia o **Status do Chamado** através de uma máquina de estados controlada:
  - `ABERTO` → `EM_ANDAMENTO` → `PARA_TESTAR` → `FECHADO`
- Cada chamado possui **histórico de comentários** e **anexos** (logs, screenshots).
- Somente **membros do projeto** podem visualizar e interagir com seus chamados.

---

## 🏗️ Arquitetura do Sistema

O sistema será dividido em duas camadas principais:

1. **Backend (API RESTful)**  
   - Responsável pela autenticação, controle de acesso, CRUD de projetos e chamados.  
   - Implementação da máquina de estados e upload de arquivos.  
   - Framework sugerido: **Flask / Django / Node.js (Express)**.

2. **Frontend (Interface Web)**  
   - Interface responsiva para interação dos usuários.  
   - Exibição de projetos, chamados e comentários.  

---

## 🚀 Funcionalidades Futuras (Ideias)

- Sistema de notificações por e-mail ou dashboard interno.  
- Filtros e busca avançada de chamados.  
- Dashboard de métricas (tempo médio de resolução, bugs por projeto, etc.).  
- Integração com ferramentas externas (ex: Slack, GitHub Issues).  

---

## 🏁 Status do Projeto
📌 Em desenvolvimento
📅 Versão inicial planejada para: A definir

---

| “O primeiro passo para resolver um bug é torná-lo visível.” 🐛
