# TO-DO Docker

## Descrição
Este projeto é uma aplicação de lista de tarefas (TO-DO) construída com Node.js, Express e PostgreSQL, e containerizada usando Docker. A aplicação permite adicionar, visualizar, marcar como concluídas e deletar tarefas. 

## Estrutura do Projeto
- `agenda/node-todo-app/public/index.html`: Página HTML principal da aplicação.
- `agenda/node-todo-app/public/app.js`: Script JavaScript para manipulação do DOM e interação com a API.
- `agenda/node-todo-app/index.js`: Servidor Node.js com endpoints para gerenciar tarefas.
- `agenda/node-todo-app/Dockerfile`: Dockerfile para construir a imagem da aplicação Node.js.
- `agenda/node-todo-app/Dockerfile-postgres`: Dockerfile para configurar o PostgreSQL.
- `agenda/node-todo-app/docker-compose.yml`: Arquivo Docker Compose para orquestrar os containers da aplicação e do banco de dados.
- `agenda/node-todo-app/volumedb`: Diretório para persistência de dados do PostgreSQL.
- `init-db.sh`: Script de inicialização do banco de dados PostgreSQL.

## Pré-requisitos
- Docker e Docker Compose instalados na máquina.

## Como Executar

1. **Clone o repositório:**

git clone https://github.com/seu-usuario/to-do-Docker.git

Agora acesse a pasta node-todo-app

```
cd to-do-Docker/agenda/node-todo-app
```

2. **Construa e inicie os containers:**

### Criando imagem do node

```
docker build -t node-todo-app .
```

### Criando imagem do postgres

```
docker build -t banco-de-dados .
```

### Executando o compose

```
docker-compose up --build
```

3. **Acesse a aplicação:**
   Abra o navegador e vá para `http://localhost:3000`.

## Endpoints da API
- **Adicionar Tarefa:**
  - **POST** `/tasks`
  - Corpo da requisição: `{ "observacao": "Descrição da tarefa" }`
  - Resposta: `{ "id": 1, "observacao": "Descrição da tarefa", "concluido": false, "data_criacao": "2023-10-01T00:00:00.000Z" }`

- **Marcar Tarefa como Concluída:**
  - **PUT** `/tasks/:id`
  - Resposta: `{ "id": 1, "observacao": "Descrição da tarefa", "concluido": true, "data_criacao": "2023-10-01T00:00:00.000Z", "data_finalizado": "2023-10-01T01:00:00.000Z" }`

- **Obter Todas as Tarefas:**
  - **GET** `/tasks`
  - Resposta: `[ { "id": 1, "observacao": "Descrição da tarefa", "concluido": false, "data_criacao": "2023-10-01T00:00:00.000Z" } ]`

- **Deletar Tarefa:**
  - **DELETE** `/tasks/:id`
  - Resposta: `{ "id": 1, "observacao": "Descrição da tarefa", "concluido": false, "data_criacao": "2023-10-01T00:00:00.000Z" }`

## Estrutura de Diretórios

```	
TO-DO-DOCKER/
├── agenda/
│ ├── node_modules/
│ ├── node-todo-app/
│ │ ├── public/
│ │ │ ├── app.js
│ │ │ └── index.html
│ │ ├── Dockerfile
│ │ ├── Dockerfile-postgres
│ │ ├── docker-compose.yml
│ │ ├── index.js
│ │ ├── package.json
│ │ ├── package-lock.json
│ │ ├── volumedb/
│ │ └── init-db.sh
└── README.md
```


## Contribuição
Sinta-se à vontade para abrir issues e pull requests para melhorias e correções.

## Licença
Este projeto está licenciado sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.