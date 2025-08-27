# 📝 Organizador de Tarefas

API REST construída com **Spring Boot** para gerenciar tarefas de forma simples.  
O projeto permite criar, listar, atualizar e excluir tarefas (CRUD).  

---

## 🚀 Tecnologias utilizadas
- Java 17+
- Spring Boot
- Spring Data JPA
- Maven
- PostgreSQL (ou H2 para testes)
- Railway (deploy)

---

## ⚙️ Como rodar o projeto localmente

### Pré-requisitos
- **Java 17+** instalado  
- **Maven** instalado  
- Banco de dados configurado (H2 por padrão, PostgreSQL no Railway)

### Passos
```bash
# Clone o repositório
git clone https://github.com/seu-usuario/organizador-de-tarefas.git

# Acesse a pasta
cd organizador-de-tarefas

# Compile e rode
mvn spring-boot:run
```

A API estará rodando em:
👉 http://localhost:8080/tarefas

### 📌 Endpoints da API
🔹 Listar todas as tarefas
GET /tarefas

🔹 Buscar tarefa por ID
GET /tarefas/{id}

🔹 Criar nova tarefa
POST /tarefas
Content-Type: application/json

{
  "titulo": "Estudar Java",
  "descricao": "Revisar POO e Spring Boot",
  "concluida": false
}

🔹 Atualizar tarefa existente
PUT /tarefas/{id}
Content-Type: application/json

{
  "titulo": "Estudar Spring Boot",
  "descricao": "Focar em JPA e REST",
  "concluida": true
}

🔹 Deletar tarefa
DELETE /tarefas/{id}

### 📊 Diagrama (Mermaid)

```mermaid
classDiagram
    class Tarefa {
        +Long id
        +String titulo
        +String descricao
        +boolean concluida
        +getId()
        +setId()
        +getTitulo()
        +setTitulo()
        +getDescricao()
        +setDescricao()
        +isConcluida()
        +setConcluida()
    }

    class TarefaRepository {
        <<interface>>
        +findAll()
        +findById(Long id)
        +save(Tarefa tarefa)
        +delete(Tarefa tarefa)
    }

    class TarefaController {
        +listarTarefas()
        +buscarTarefa(Long id)
        +criarTarefa(Tarefa tarefa)
        +atualizarTarefa(Long id, Tarefa tarefa)
        +deletarTarefa(Long id)
    }

    TarefaController --> TarefaRepository
    TarefaRepository --> Tarefa

    TarefaController --> Tarefa
