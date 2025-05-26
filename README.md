# 📚 Projeto de Estudos JPA

Um projeto simples e prático para fixação dos conceitos fundamentais de **Java Persistence API (JPA)** com **Hibernate** e **MySQL**.

## 🎯 Objetivo

Este projeto foi desenvolvido com o propósito de **auto-fixação** dos conteúdos estudados sobre JPA, demonstrando na prática:

- Configuração de um projeto JPA com Maven
- Mapeamento de entidades 
- Operações básicas de CRUD
- Gerenciamento de transações
- Configuração de persistência

## 🛠️ Tecnologias Utilizadas

![Java](https://img.shields.io/badge/Java-23-orange?style=flat-square&logo=java)
![Hibernate](https://img.shields.io/badge/Hibernate-6.4.4-green?style=flat-square&logo=hibernate)
![MySQL](https://img.shields.io/badge/MySQL-8.0+-blue?style=flat-square&logo=mysql)
![Maven](https://img.shields.io/badge/Maven-Build_Tool-red?style=flat-square&logo=apache-maven)

- **Java 23** - Linguagem de programação
- **JPA (Jakarta Persistence API)** - API de persistência
- **Hibernate 6.4.4** - Implementação JPA
- **MySQL 8.4** - Banco de dados relacional
- **Maven** - Gerenciamento de dependências

## 📁 Estrutura do Projeto

```
aulajpamaven/
├── src/
│   └── main/
│       ├── java/
│       │   ├── br/com/kaudotdev/
│       │   │   └── Main.java              # Classe principal
│       │   └── dominio/
│       │       └── Pessoa.java            # Entidade JPA
│       └── resources/
│           └── META-INF/
│               └── persistence.xml        # Configuração JPA
├── pom.xml                               # Configuração Maven
└── README.md
```

## 🗃️ Modelo de Dados

### Entidade Pessoa

```java
@Entity
public class Pessoa {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;
    private String name;
    private String email;
    
    // construtores, getters, setters...
}
```

**Campos:**
- `id` - Chave primária (auto incremento)
- `name` - Nome da pessoa
- `email` - Email da pessoa

## ⚙️ Configuração

### Banco de Dados

O projeto está configurado para usar **MySQL** com as seguintes configurações padrão:

- **Host:** localhost:3306
- **Database:** aulajpa
- **User:** root
- **Password:** (vazio)

### Variáveis de Ambiente (Opcionais)

Você pode personalizar a configuração usando variáveis de ambiente:

```bash
DB_URL=jdbc:mysql://localhost:3306/aulajpa
DB_USER=root
DB_PASSWORD=sua_senha
HIBERNATE_DDL_AUTO=update
SHOW_SQL=true
FORMAT_SQL=true
```

## 🚀 Como Executar

### Pré-requisitos

- Java 23+ instalado
- MySQL 8.0+ instalado e rodando
- Maven 3.6+ instalado

### Passos

1. **Clone o projeto**
   ```bash
   git clone <url-do-repositorio>
   cd aulajpamaven
   ```

2. **Configure o banco de dados**
   ```sql
   CREATE DATABASE aulajpa;
   ```

3. **Execute o projeto**
   ```bash
   mvn compile exec:java -Dexec.mainClass="br.com.kaudotdev.Main"
   ```

## 💡 Funcionalidades Implementadas

### ✅ Operações Demonstradas

- **Busca por ID** - `em.find(Pessoa.class, id)`
- **Remoção de Entidade** - `em.remove(entity)`
- **Gerenciamento de Transação** - `begin()`, `commit()`
- **Fechamento de Recursos** - `em.close()`, `emf.close()`

### 🔄 Fluxo do Programa Principal

```java
// 1. Criar EntityManagerFactory
EntityManagerFactory emf = Persistence.createEntityManagerFactory("exemplo-jpa");

// 2. Obter EntityManager
EntityManager em = emf.createEntityManager();

// 3. Buscar entidade por ID
Pessoa p = em.find(Pessoa.class, 2);

// 4. Iniciar transação e remover
em.getTransaction().begin();
em.remove(p);
em.getTransaction().commit();

// 5. Fechar recursos
em.close();
emf.close();
```

## 📝 Conceitos Estudados

### 🎓 Tópicos Abordados

- **Entity Manager**: Gerenciamento do contexto de persistência
- **Persistence Unit**: Configuração da unidade de persistência
- **Entity Lifecycle**: Estados das entidades (Transient, Persistent, Detached, Removed)
- **Transactions**: Controle de transações com JPA
- **ID Generation**: Estratégias de geração de chaves primárias
- **Database Configuration**: Configuração de conexão com banco

### 🔍 Pontos de Aprendizado

- Configuração do `persistence.xml`
- Anotações JPA básicas (`@Entity`, `@Id`, `@GeneratedValue`)
- Gerenciamento manual de transações
- Padrão de fechamento de recursos
- Integração Maven com JPA

## 🎯 Próximos Passos de Estudo

- [ ]  Implementar operações de **Create** e **Update**
- [ ]  Explorar **JPQL** (Java Persistence Query Language)
- [ ]  Estudar **relacionamentos** entre entidades
- [ ]  Implementar **DAO Pattern**
- [ ]  Adicionar **validações** com Bean Validation
- [ ]  Explorar **cache** de segundo nível

## 📚 Recursos de Estudo

- [Documentação oficial JPA](https://jakarta.ee/specifications/persistence/)
- [Guia do Hibernate](https://hibernate.org/orm/documentation/)
- [Tutorial JPA - Oracle](https://docs.oracle.com/javaee/7/tutorial/persistence-intro.htm)

---

**📌 Nota:** Este é um projeto de estudos focado na **fixação de conceitos** de JPA. O código é simples e direto, priorizando a clareza e o entendimento dos fundamentos da persistência em Java.

---
*Desenvolvido por [Kaudotdev](https://github.com/kaudotdev) como material de estudo* 🚀
