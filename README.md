<h1 align="center">💪 Trainify</h1>

<p align="center"><i>API para gerenciamento de academias, projetada para facilitar a conexão entre usuários e estabelecimentos fitness.</i>
  <br/><br/>
  <img src="https://img.shields.io/github/last-commit/joschonarth/trainify?style=default&logo=git&logoColor=white&color=0080ff&labelColor=2f363d" alt="last-commit">
	<img src="https://img.shields.io/github/languages/top/joschonarth/trainify?style=default&color=0080ff&labelColor=2f363d" alt="repo-top-language">
	<img src="https://img.shields.io/github/languages/count/joschonarth/trainify?style=default&color=0080ff&labelColor=2f363d" alt="repo-language-count">
  <img src="https://github.com/joschonarth/trainify/actions/workflows/run-unit-tests.yml/badge.svg?style=for-the-badge&color=a277ff&labelColor=1C1E26" alt="unit-tests">
  <img src="https://github.com/joschonarth/trainify/actions/workflows/run-e2e-tests.yml/badge.svg?style=for-the-badge&color=a277ff&labelColor=1C1E26" alt="e2e-tests">
</p>

## 📑 Índice

- [👀 Visão Geral](#-visão-geral)
- [🛠️ Tecnologias Utilizadas](#️-tecnologias-utilizadas)
- [⚙️ Funcionalidades](#️-funcionalidades)
- [🚀 Como Executar o Projeto](#-como-executar-o-projeto)
- [🔗 Endpoints](#-endpoints)
- [🔐 Autenticação](#-autenticação)
- [🧪 Testes](#-testes)
- [⚙️ GitHub Actions](#️-github-actions)
- [🤝 Contribuições](#-contribuições)
- [⭐ Apoie este Projeto](#-apoie-este-projeto)
- [📞 Contato](#-contato)

# 👀 Visão Geral

**Trainify** é uma solução robusta para gerenciamento de academias, proporcionando funcionalidades essenciais como registro de usuários, autenticação, localização de academias próximas e controle de check-ins. Inspirada em plataformas como o GymPass, esta API oferece uma experiência eficiente e segura para academias e seus frequentadores.

## 🛠️ Tecnologias Utilizadas

- 🟢 **Node.js**: Plataforma para execução do JavaScript no servidor.
- 🟦 **TypeScript**: Superset do JavaScript com tipagem estática.
- ⚡ **Fastify**: Framework web de alta performance para Node.js.
- 🗄️ **PostgreSQL**: Banco de dados relacional utilizado para armazenar informações.
- 🛢️ **Prisma**: ORM moderno para interações com o banco de dados.
- 🐳 **Docker**: Containerização para ambiente de desenvolvimento.
- 💎 **Zod**: Validação de esquemas e dados.
- 🛡️ **JWT**: Json Web Tokens para autenticação.
- 🧪 **Vitest**: Framework de testes.
- 🕷️ **Supertest**: Biblioteca para testar APIs de forma simples e eficaz.
- 🔨 **Tsup**: Ferramenta para bundling.
- ⚙️ **ESLint**: Linter para garantir a qualidade do código.
- 🔒 **Bcrypt**: Biblioteca para hashing de senhas.
- 📅 **Day.js**: Manipulação de datas.
- 🌱 **Dotenv**: Gerenciamento de variáveis de ambiente.
- ⚙️ **GitHub Actions**: Ferramenta de CI que automatiza o processo de testes e implantações.

## ⚙️ Funcionalidades

### Usuários

- 🎉 **Criar usuário**: Cria um novo usuário na plataforma.
- 🔐 **Autenticar usuário**: Realiza o login de um usuário existente.
- 🔄 **Refresh token**: Gera um novo token de autenticação.
- 👤 **Ver perfil**: Retorna as informações do perfil do usuário autenticado.

### Academias

- 🏋️ **Criar academia**: Adiciona uma nova academia ao sistema.
- 🔍 **Buscar academias**: Localiza academias com base em critérios de pesquisa.
- 📍 **Listar academias próximas**: Retorna academias localizadas nas proximidades do usuário.

### Check-ins

- ✅ **Criar check-in**: Registra a presença do usuário em uma academia.
- 📜 **Histórico de check-ins**: Exibe o histórico de check-ins do usuário.
- 📊 **Métricas de check-ins**: Fornece dados sobre a quantidade total de check-ins realizados.
- ✔️ **Validar check-in**: Confirma a validade de um check-in.

## 🚀 Como Executar o Projeto

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/joschonarth/trainify.git
   ```

2. **Crie um arquivo `.env` a partir do exemplo:**

    ```bash
    cp .env.example .env
    ```

    Edite o arquivo `.env` para configurar as variáveis de ambiente necessárias.

3. **Instale as dependências:**

    ```bash
    npm install
    ```

4. Inicie o banco de dados **PostgreSQL** utilizando o container **Docker** com a imagem ``bitnami/postgresql``:

   ```bash
   docker-compose up -d
   ```

5. **Execute as migrações do banco de dados:**

   ```bash
   npx prisma migrate dev
   ```

6. **Inicie a API:**

   ```bash
   npm run start:dev
   ```

   A aplicação estará disponível em [http://localhost:3333](http://localhost:3333).

## 🔗 Endpoints

### 🎉 Criar Usuário

- **Descrição:** Cria um novo usuário na plataforma.
- **Método:** `POST`
- **URL:** `/users`
- **Corpo da Requisição:**  

  ```json
  {
    "name": "John Doe",
    "email": "johndoe@example.com",
    "password": "123456"
  }
  ```

### 🔐 Autenticar Usuário

- **Descrição:** Realiza o login de um usuário existente.
- **Método:** `POST`
- **URL:** `/sessions`
- **Corpo da Requisição:**

  ```json
  {
    "email": "johndoe@example.com",
    "password": "123456"
  }
  ```

- **Exemplo de Resposta:**  

  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR..."
  }
  ```

### 🔄 Refresh Token

- **Descrição:** Gera um novo token de autenticação.
- **Método:** `PATCH`
- **URL:** `/token/refresh`
- **Corpo da Requisição:**  

- **Exemplo de Resposta:**  

  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR..."
  }
  ```

### 👤 Ver Perfil

- **Descrição:** Retorna as informações do perfil do usuário autenticado.
- **Método:** `GET`
- **URL:** `/me`
- **Exemplo de Resposta:**  

  ```json
  {
    "user": {
        "id": "be48f670-7df1-44b8-b4c0-7f6722978ed6",
        "name": "John Doe",
        "email": "johndoe@gmail.com",
        "role": "MEMBER",
        "created_at": "2025-02-24T17:53:17.994Z"
    }
  }
  ```

### 🏋️ Criar Academia

- **Descrição:** Adiciona uma nova academia ao sistema.
- **Método:** `POST`
- **URL:** `/gyms`
- **Corpo da Requisição:**  

  ```json
  {
    "title": "TypeScript Gym",
    "description": "Some description",
    "phone": "11999999999",
    "latitude": -20.7400886,
    "longitude": -47.753894
  }
  ```

### 🔍 Buscar Academias

- **Descrição:** Localiza academias com base em critérios de pesquisa.
- **Método:** `GET`
- **URL:** `/gyms/search`
- **Query Params:**
  - `q` (string, required): Termo de pesquisa para filtrar academias pelo título ou descrição.
  - `page` (number, optional): Número da página para paginação dos resultados.

- **Exemplo de Requisição:**

  ```http
  GET /gyms/search?q=TypeScript&page=1
  ```

- **Exemplo de Resposta:**  

  ```json
  {
    "gyms": [
        {
            "id": "8a83ce21-250f-443e-ac06-a1061c9ffb0c",
            "title": "TypeScript Gym",
            "description": "Some description",
            "phone": "11999999999",
            "latitude": "-20.7400886",
            "longitude": "-47.753894"
        }
    ]
  }
  ```

### 📍 Listar Academias Próximas

- **Descrição:** Retorna academias localizadas nas proximidades do usuário.
- **Método:** `GET`
- **URL:** `/gyms/nearby`
- **Parâmetros de Consulta:**
  - ``latitude`` (number, required) - Latitude atual do usuário (deve estar entre -90 e 90).
  - ``longitude`` (number, required) - Longitude atual do usuário (deve estar entre -180 e 180).

- **Exemplo de Requisição:**
  
  ```http
  GET /gyms/nearby?latitude=-20.7400886&longitude=-47.753894
  ```

- **Exemplo de Resposta:**

  ```json
  {
    "gyms": [
        {
            "id": "8a83ce21-250f-443e-ac06-a1061c9ffb0c",
            "title": "TypeScript Gym",
            "description": "Some description",
            "phone": "11999999999",
            "latitude": "-20.7400886",
            "longitude": "-47.753894"
        },
        {
            "id": "1aedfe5a-4aa1-452a-b0c2-b40c4b74b8a4",
            "title": "JavaScript Gym",
            "description": "Some description",
            "phone": "11999999999",
            "latitude": "-20.7400886",
            "longitude": "-47.753894"
        }
    ]
  }
  ```

### ✅ Criar Check-in

- **Descrição:** Registra a presença do usuário em uma academia.
- **Método:** `POST`
- **URL:** `/gyms/:gymId/check-ins`
- **Corpo da Requisição:**  

  ```json
  {
    "latitude": -20.7400886,
    "longitude": -47.753894
  }
  ```

### 📜 Histórico de Check-ins

- **Descrição:** Exibe o histórico de check-ins do usuário.
- **Método:** `GET`
- **URL:** `/check-ins/history`
- **Query Params:**
  - `page` (number, optional): Número da página para paginação dos resultados.

- **Exemplo de Resposta:**  

  ```json
  {
    "checkIns": [
        {
            "id": "ccfd55a9-9eb2-4d05-9b0b-ef19e70165f5",
            "created_at": "2025-02-24T18:29:52.436Z",
            "validated_at": null,
            "user_id": "be48f670-7df1-44b8-b4c0-7f6722978ed6",
            "gym_id": "8a83ce21-250f-443e-ac06-a1061c9ffb0c"
        }
    ]
  }
  ```

### 📊 Métricas de Check-ins

- **Descrição:** Fornece dados sobre a quantidade total de check-ins realizados.
- **Método:** `GET`
- **URL:** `/check-ins/metrics`
- **Exemplo de Resposta:**  

  ```json
  {
    "checkInsCount": 1
  }
  ```

### ✔️ Validar Check-in

- **Descrição:** Confirma a validade de um check-in.
- **Método:** `PATCH`
- **URL:** `/check-ins/:checkInId/validate`

## 🔐 Autenticação

As rotas da API estão protegidas por autenticação **JWT** (JSON Web Token). Para acessar as rotas que requerem autenticação, é necessário obter um token de acesso.

### Como se autenticar

1. **Faça a autenticação** com suas credenciais (email e senha) na rota `/sessions` para obter um token JWT:

    - **Método**: `POST`
    - **URL**: `/sessions`
    - **Corpo da Requisição:**

    ```json
    {
        "email": "user@email.com",
        "password": "password"
    }
    ```

    - **Resposta**:

    ```json
    {
        "token": "your_token"
    }
    ```

2. **Utilize o token** nas requisições às rotas protegidas, incluindo-o no Postman (ou outro API Client) da seguinte forma:

    - No Postman, vá até a aba **Authorization**.
    - Selecione o tipo **Bearer Token**.
    - No campo **Token**, insira o valor do seu token JWT obtido no passo anterior.

### ⚖️ Autorização por Cargos (RBAC)

A aplicação implementa uma autorização baseada em cargos (**RBAC** - Role-Based Access Control). Algumas rotas, como a de **criar academia** e **validar check-in**, requerem que o usuário tenha a role **ADMIN** para serem acessadas. Portanto, certifique-se de que sua conta possui as permissões necessárias para executar essas ações.

## 🧪 Testes

Este projeto inclui **testes unitários** e **testes E2E** (end-to-end) para garantir a confiabilidade e o funcionamento correto dos recursos implementados. Para executar os testes, utilize os seguintes comandos:

- **Executar testes unitários:**

  ```bash
  npm run test
  ```

- **Executar testes unitários em modo de observação:**

  ```bash
  npm run test:watch
  ```

- **Preparar o ambiente do Prisma antes dos testes E2E:**

  ```bash
  npm run pretest:e2e
  ```

- **Executar testes E2E:**

  ```bash
  npm run test:e2e
  ```

- **Executar testes E2E em modo de observação:**

  ```bash
  npm run test:e2e:watch
  ```

- **Executar testes com cobertura:**

  ```bash
  npm run test:coverage
  ```

- **Executar a interface do usuário do Vitest:**

  ```bash
  npm run test:ui
  ```

## ⚙️ GitHub Actions

O projeto utiliza o **GitHub Actions** para automação de testes, garantindo qualidade contínua no desenvolvimento. Os **testes unitários** são executados automaticamente a cada ``push`` para o repositório, enquanto os **testes E2E** são acionados em cada ``pull request``. Essa configuração assegura que todas as alterações sejam validadas, promovendo um fluxo de trabalho eficiente e livre de erros.

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests com melhorias ou correções. ✨

## ⭐ Apoie este Projeto

Se este projeto te ajudou ou te inspirou de alguma forma, não esqueça de deixar uma ⭐ no repositório! Isso faz toda a diferença! 🚀

## 📞 Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joschonarth/)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:joschonarth@gmail.com)