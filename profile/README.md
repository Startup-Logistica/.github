---

# **Projeto StartupLogistica - Sistema de Gerenciamento de Usuários**

## **Descrição do Projeto**

O **Sistema de Gerenciamento de Usuários** da **StartupLogistica** visa fornecer uma plataforma ágil para autenticação e gerenciamento de usuários. O projeto inclui tanto o **frontend** quanto o **backend**, e permite que os usuários realizem ações como registro, login, edição e exclusão de perfis.

O sistema utiliza **autenticação via JWT** para garantir a segurança dos dados, com uma interface simples e responsiva desenvolvida em **HTML**, **CSS** e **JavaScript**. O **backend** foi desenvolvido utilizando **Java 21**, **Spring Boot**, e **PostgreSQL**, oferecendo uma API REST que gerencia usuários e autenticação.

### **Objetivo**

O objetivo principal deste projeto é criar uma plataforma que permita a gestão de usuários com funcionalidades como:

* **Autenticação de usuários via JWT**.
* **Cadastro de novos usuários**.
* **Listagem, edição e exclusão de perfis**.

Este projeto exemplifica o uso de **metodologias ágeis**, como **Kanban**, para a organização e desenvolvimento contínuo das funcionalidades.

---

## **Metodologia Utilizada**

Durante o desenvolvimento do projeto, foi adotada a metodologia **Kanban**, utilizando a aba **Projects** no GitHub para gerenciar o fluxo de trabalho. O quadro Kanban foi dividido nas seguintes colunas:

* **A Fazer**: Backlog de funcionalidades e ajustes de UI.
* **Em Progresso**: Funcionalidades sendo implementadas.
* **Concluído**: Funcionalidades finalizadas e testadas.

---

## **Estrutura de Diretórios**

### **Frontend** (HTML, CSS, JavaScript)

```plaintext
/public
├── login.html       # Tela de login com botão “Cadastrar-se”
├── cadastro.html    # Tela de cadastro público de novos usuários
├── usuarios.html    # Listagem de usuários, edição em modal e exclusão
└── css
    └── styles.css   # Estilos compartilhados
└── js
    ├── login.js     # Lógica de login e redirecionamento
    ├── cadastro.js  # Lógica de cadastro de usuários
    └── usuarios.js  # Fetch de dados, modal de edição e exclusão
```

### **Backend** (Java 21, Spring Boot, PostgreSQL)

```plaintext
/src
├── main
│   ├── java
│   │   └── com
│   │       └── startup
│   │           └── logistica
│   │               ├── config        # Configurações do Spring Boot
│   │               ├── dtos          # Data Transfer Objects (DTOs)
│   │               ├── entities     # Entidades JPA
│   │               ├── enums         # Enumerações do sistema
│   │               ├── errors        # Tratamento de erros
│   │               ├── mappers       # Mapeamento entre DTOs e Entidades
│   │               ├── repositories  # Interfaces de repositório
│   │               ├── rest          # Controladores e Especificações REST
│   │               ├── security      # Segurança (configuração do JWT)
│   │               ├── services      # Lógica de negócio
│   │               └── usecases      # Casos de uso do sistema
│   └── resources
│       └── application.properties      # Configurações do Spring Boot
```

---

## **Dependências**

### **Frontend**:

* **Fonte**: Noto Sans (Google Fonts).
* **Servidor Estático**: Pode usar qualquer um dos seguintes servidores:

  * **Live Server (VS Code)**.
  * **http-server (Node.js)**.
  * **Python http.server**.

### **Backend**:

* **Java 21**.
* **Spring Boot 2.x**.
* **Spring Security** (para autenticação via JWT).
* **PostgreSQL** (para armazenar os dados dos usuários).
* **Spring Data JPA** (para integração com o banco de dados).
* **Lombok** (para reduzir a verbosidade do código).
* **H2 Database** (usado para testes e desenvolvimento local, se necessário).

---

## **Instruções para Execução**

### **Frontend**

1. Clone ou copie apenas a pasta `public` do repositório para sua máquina.

2. Abra um terminal na pasta raiz do frontend.

3. Inicie um servidor estático:

   * **Live Server (VS Code)**: Clique com o botão direito em qualquer arquivo `.html` → **Open with Live Server**.
   * **http-server (Node.js)**:

     ```bash
     npm install -g http-server
     http-server . -c-1
     ```
   * **Python 3**:

     ```bash
     python3 -m http.server 5500
     ```

4. Acesse as telas no navegador:

   * **Tela de Login**: [http://127.0.0.1:5500/login.html](http://127.0.0.1:5500/login.html).
   * **Tela de Cadastro**: [http://127.0.0.1:5500/cadastro.html](http://127.0.0.1:5500/cadastro.html).
   * Após login, será redirecionado para **usuarios.html** → Listagem de usuários.

---

### **Backend**

1. Clone o repositório com o backend.

2. Abra um terminal na pasta do backend e execute:

   ```bash
   mvn install
   mvn spring-boot:run
   ```

3. O **backend** estará rodando em **[http://localhost:8080/api/v1](http://localhost:8080/api/v1)**. Certifique-se de que as rotas CORS estejam configuradas corretamente para permitir o acesso do frontend.

4. A configuração do banco de dados **PostgreSQL** deve estar no arquivo **application.properties**, com as credenciais corretas.

---

## **Funcionalidades**

### **Login (login.html)**

* Envia um **POST** para `/api/v1/login`, armazena o token JWT e redireciona para a página de listagem de usuários.
* O botão **Cadastrar-se** leva o usuário para a página de cadastro.

### **Cadastro (cadastro.html)**

* Envia um **POST** para `/api/v1/users` sem necessidade de token JWT.
* Após o cadastro bem-sucedido, redireciona para a tela de login.

### **Listagem de Usuários (usuarios.html)**

* Exibe uma tabela de usuários através de um **GET** para `/api/v1/users?page=0&limit=1000`.
* O cabeçalho exibe a mensagem de boas-vindas com o nome do usuário através de **GET /api/v1/user**.
* Possui os botões:

  * **Novo Usuário**.
  * **Editar** (abre um modal de edição).
  * **Deletar** (deleta o usuário).
  * **Sair**.

---

## **Customização de Estilo**

* **Cores**:

  * Fundo escuro: **#201b2c**.
  * Destaque em verde: **#00ff88**.
* **Responsividade**:

  * **Media queries** para telas menores que 950px e 600px.

---

## **Observação Importante**

Certifique-se de que o **backend** esteja rodando em **[http://localhost:8080/api/v1](http://localhost:8080/api/v1)** e com **CORS configurado** para **[http://127.0.0.1:5500](http://127.0.0.1:5500)**.

---

## **Controle de Qualidade**

A configuração do **GitHub Actions** para testes automatizados está presente no repositório. O pipeline garante que a API seja validada sempre que uma alteração for realizada.

---

## **Simulação de Mudança no Escopo**

Durante o desenvolvimento, o escopo do projeto foi alterado para incluir a **autenticação JWT** e a **integração com GitHub Actions** para garantir a qualidade contínua do código.

### **Justificativa da Mudança**:

A decisão de implementar a autenticação JWT foi motivada pela necessidade de proteger os dados dos usuários e garantir uma experiência mais segura ao acessar as funcionalidades do sistema. Além disso, a integração com o **GitHub Actions** foi adicionada para melhorar a qualidade do código e garantir que todas as alterações sejam validadas automaticamente por testes, evitando a introdução de erros no código principal.

### **Alteração no Quadro Kanban**:

As tarefas relacionadas à implementação de autenticação JWT e à configuração do pipeline de CI com **GitHub Actions** foram movidas para a coluna **Em Progresso** e, após finalização, para a coluna **Concluído** no quadro **Kanban** do GitHub Projects.

---

## **Vídeo Explicativo**

O vídeo explicativo pode ser acessado no [link do vídeo](#).

---
