# 🛍️ API Vitrine E-commerce

<div align="center">

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ_IDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)

**Uma API RESTful moderna e robusta para gerenciamento de vitrine de e-commerce**

[Recursos](#-recursos) • [Tecnologias](#️-tecnologias) • [Instalação](#-instalação) • [Como Usar](#-como-usar) • [API Endpoints](#-api-endpoints)

</div>

---

## 📋 Sobre o Projeto

A **API Vitrine E-commerce** é uma solução backend completa para gerenciar produtos, categorias e a vitrine de uma loja virtual. Desenvolvida com as melhores práticas de desenvolvimento, oferece endpoints eficientes e seguros para operações de CRUD.

## ✨ Recursos

- ✅ **Gerenciamento de Produtos** - CRUD completo com validações
- ✅ **Categorização Inteligente** - Organização por categorias
- ✅ **Busca Avançada** - Filtros e paginação otimizados
- ✅ **Containerização** - Deploy simplificado com Docker
- ✅ **API RESTful** - Seguindo padrões REST
- ✅ **Documentação Automática** - Swagger/OpenAPI integrado
- ✅ **Build Automatizado** - Gradle para gestão de dependências

## 🛠️ Tecnologias

Este projeto foi desenvolvido com as seguintes tecnologias:

| Tecnologia | Descrição |
|------------|-----------|
| **Java** | Linguagem de programação principal |
| **Spring Boot** | Framework para criação de aplicações Java |
| **Gradle** | Ferramenta de automação de build |
| **Docker** | Containerização e deploy da aplicação |
| **IntelliJ IDEA** | IDE utilizada no desenvolvimento |
| **PostgreSQL/MySQL** | Banco de dados relacional |

## 📦 Instalação

### Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- [Java JDK 21+](https://www.oracle.com/java/technologies/downloads/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/)

### Clonando o Repositório

```bash
git clone https://github.com/seu-usuario/api-vitrine-ecommerce.git
cd api-vitrine-ecommerce
```

### Executando com Docker

```bash
# Build da imagem
docker build -t api-vitrine-ecommerce .

# Executar o container
docker run -p 8080:8080 api-vitrine-ecommerce
```

**Ou usando Docker Compose:**

```bash
docker-compose up -d
```

### Executando Localmente

```bash
# Dar permissão ao gradlew (Linux/Mac)
chmod +x gradlew

# Instalar dependências e buildar
./gradlew build

# Executar a aplicação
./gradlew bootRun
```

**Para Windows:**

```bash
gradlew.bat build
gradlew.bat bootRun
```

### Exemplo de Requisições

```bash
# Listar todos os produtos
curl -X GET http://localhost:8080/api/produtos

# Buscar produto por ID
curl -X GET http://localhost:8080/api/produtos/1

# Criar um novo produto
curl -X POST http://localhost:8080/api/produtos \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Notebook Gamer",
    "descricao": "Notebook de alta performance",
    "preco": 4999.99,
    "estoque": 10,
    "categoria": "Eletrônicos"
  }'

# Atualizar produto
curl -X PUT http://localhost:8080/api/produtos/1 \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "Notebook Gamer Atualizado",
    "preco": 4599.99
  }'

# Deletar produto
curl -X DELETE http://localhost:8080/api/produtos/1
```

## 📍 API Endpoints

### Produtos

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/api/produtos` | Lista todos os produtos |
| GET | `/api/produtos/{id}` | Busca produto por ID |
| GET | `/api/produtos/buscar?nome={nome}` | Busca produtos por nome |
| POST | `/api/produtos` | Cria novo produto |
| PUT | `/api/produtos/{id}` | Atualiza produto |
| DELETE | `/api/produtos/{id}` | Remove produto |

### Categorias

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/api/categorias` | Lista todas as categorias |
| GET | `/api/categorias/{id}` | Busca categoria por ID |
| POST | `/api/categorias` | Cria nova categoria |
| PUT | `/api/categorias/{id}` | Atualiza categoria |
| DELETE | `/api/categorias/{id}` | Remove categoria |

### Vitrine

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/api/vitrine` | Lista produtos em destaque |
| GET | `/api/vitrine/promocoes` | Lista produtos em promoção |

## 📂 Estrutura do Projeto

```
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── ecommerce/
│   │           ├── controller/      # Controllers REST
│   │           ├── model/           # Entidades JPA
│   │           ├── repository/      # Repositórios Spring Data
│   │           ├── service/         # Lógica de negócio
│   │           ├── dto/             # Data Transfer Objects
│   │           ├── config/          # Configurações
│   │           └── exception/       # Tratamento de exceções
│   └── resources/
│       ├── application.yml   # Configurações da aplicação
│       └── application-dev.yml
├── test/
│   └── java/                        # Testes unitários e integração
├── build.gradle                      # Configuração do Gradle
├── Dockerfile                        # Configuração Docker
└── docker-compose.yml               # Orquestração de containers
```

## 🐳 Docker

### Dockerfile

```dockerfile
FROM openjdk:21-jdk-slim
WORKDIR /app
COPY build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```

### Build e Run

```bash
# Build do projeto com Gradle
./gradlew clean build

# Build da imagem Docker
docker build -t api-vitrine-ecommerce .

# Executar container
docker run -p 8080:8080 api-vitrine-ecommerce
```

## 🧪 Testes

```bash
# Executar todos os testes
./gradlew test

# Executar testes com relatório de cobertura
./gradlew test jacocoTestReport

# Ver relatório de cobertura
open build/reports/jacoco/test/html/index.html
```

## 🔧 Configuração

Edite o arquivo `application.yml` para configurar:

```properties
# Porta da aplicação
server.port=8080

# Banco de dados
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

1. Faça um Fork do projeto
2. Crie sua Feature Branch (`git checkout -b feature/NovaFuncionalidade`)
3. Commit suas mudanças (`git commit -m 'Add: Nova funcionalidade'`)
4. Push para a Branch (`git push origin feature/NovaFuncionalidade`)
5. Abra um Pull Request


<div align="center">

**Se este projeto foi útil, deixe uma ⭐!**

 [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diego-camargo-88aa34294/)

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Diegodccs)
</div>
