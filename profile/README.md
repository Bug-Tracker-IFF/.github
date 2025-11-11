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

## ⚙️ Requisitos Funcionais (RFs)

| Código | Descrição |
|--------|------------|
| **RF-01** | O Gerente cria Projetos e adiciona Membros (relação ManyToMany). |
| **RF-02** | Qualquer Membro pode criar um Chamado (Bug) e anexar arquivos (logs, screenshots). |
| **RF-03** | O Gerente pode atribuir o Chamado a um Desenvolvedor. |
| **RF-04** | O Chamado deve transitar por status: `ABERTO` → `EM_ANDAMENTO` → `RESOLVIDO` → `FECHADO`. |

---

## 🧠 Requisitos Não Funcionais (RNFs)

| Código | Descrição |
|--------|------------|
| **RNF-01** | **Integridade/Robustez:** A transição de status do Chamado deve ser controlada por uma **Máquina de Estado rigorosa**. *(Desafio C3)* |
| **RNF-02** | **Armazenamento:** O backend deve permitir **upload de arquivos** de log (.txt) e **imagens** (screenshots). *(Desafio C6)* |

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
   - Framework sugerido: **React / Vue / Angular**.

---

## 🧾 Estrutura de Dados (Resumo)

**Entidades principais:**
- `Usuario`
- `Projeto`
- `Chamado`
- `Comentario`
- `Anexo`

**Relacionamentos:**
- `Usuario` ↔️ `Projeto` → ManyToMany  
- `Projeto` ↔️ `Chamado` → OneToMany  
- `Chamado` ↔️ `Comentario` → OneToMany  
- `Chamado` ↔️ `Anexo` → OneToMany  

---

## 🚀 Funcionalidades Futuras (Ideias)

- Sistema de notificações por e-mail ou dashboard interno.  
- Filtros e busca avançada de chamados.  
- Dashboard de métricas (tempo médio de resolução, bugs por projeto, etc.).  
- Integração com ferramentas externas (ex: Slack, GitHub Issues).  

---

## 🧑‍💻 Execução Local (Exemplo de Setup)

```bash
# Clonar o repositório
git clone https://github.com/<sua-organizacao>/bug-tracker.git

# Entrar na pasta do projeto
cd bug-tracker

# Instalar dependências
npm install    # ou pip install -r requirements.txt

# Executar o servidor
npm start      # ou flask run
```

---

## 🏁 Status do Projeto
📌 Em desenvolvimento
📅 Versão inicial planejada para: [entrega do trabalho]

---

## 📄 Licença

Este projeto é de uso acadêmico e está licenciado sob a MIT License.
Sinta-se livre para reutilizar e adaptar para fins educacionais.

---

| “O primeiro passo para resolver um bug é torná-lo visível.” 🐛
