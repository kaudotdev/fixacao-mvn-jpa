# 🚀 Projeto JPA com Maven

Um projeto de exemplo demonstrando o uso do Jakarta Persistence API (JPA) com Hibernate e MySQL, construído com Maven.

## 📋 Descrição

Este projeto ilustra as operações básicas de persistência usando JPA/Hibernate, incluindo configuração de entidades, conexão com banco de dados MySQL e operações de CRUD. O exemplo atual demonstra a operação de **exclusão** de uma entidade `Pessoa`.

## 🛠️ Tecnologias Utilizadas

- **Java 23** - Linguagem de programação
- **Jakarta Persistence API (JPA)** - Especificação para persistência de dados
- **Hibernate 6.4.4** - Implementação JPA
- **MySQL** - Sistema de gerenciamento de banco de dados
- **Maven** - Gerenciador de dependências e build

## 📁 Estrutura do Projeto

```
src/
├── main/
│   ├── java/
│   │   ├── br/com/kaudotdev/
│   │   │   └── Main.java
│   │   └── dominio/
│   │       └── Pessoa.java
│   └── resources/
│       └── META-INF/
│           └── persistence.xml
└── pom.xml
```

## 🎯 Funcionalidades

- ✅ Configuração de entidade JPA (`@Entity`)
- ✅ Mapeamento objeto-relacional
- ✅ Operações de exclusão de registros
- ✅ Gerenciamento de transações
- ✅ Configuração flexível via variáveis de ambiente

## ⚙️ Configuração

### Pré-requisitos

- Java 23 ou superior
- MySQL Server
- Maven 3.6+

### Banco de Dados

Certifique-se de que o MySQL está rodando e crie o banco de dados:

```sql
CREATE DATABASE aulajpa;
```

### Variáveis de Ambiente (Opcional)

O projeto suporta configuração via variáveis de ambiente:

```bash
# Configurações do Banco de Dados
export DB_URL="jdbc:mysql://localhost:3306/aulajpa?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true"
export DB_USER="root"
export DB_PASSWORD="sua_senha"

# Configurações do Hibernate
export HIBERNATE_DDL_AUTO="update"
export HIBERNATE_DIALECT="org.hibernate.dialect.MySQLDialect"
export SHOW_SQL="true"
export FORMAT_SQL="true"
```

## 🚀 Como Executar

1. **Clone o repositório:**
   ```bash
   git clone [url-do-repositorio]
   cd aulajpamaven
   ```

2. **Compile o projeto:**
   ```bash
   mvn clean compile
   ```

3. **Execute a aplicação:**
   ```bash
   mvn exec:java -Dexec.mainClass="br.com.kaudotdev.Main"
   ```

## 📊 Entidade Pessoa

A entidade `Pessoa` representa um modelo simples com os seguintes atributos:

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `id` | Integer | Chave primária (auto-incremento) |
| `name` | String | Nome da pessoa |
| `email` | String | E-mail da pessoa |

### Exemplo de Uso

```java
// Buscar uma pessoa por ID
Pessoa pessoa = em.find(Pessoa.class, 2);

// Iniciar transação
em.getTransaction().begin();

// Remover a pessoa
em.remove(pessoa);

// Confirmar transação
em.getTransaction().commit();
```

## 🔧 Dependências Maven

```xml
<dependencies>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>6.4.4.Final</version>
    </dependency>
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
        <version>8.4.0</version>
    </dependency>
</dependencies>
```

## 📝 Configuração do Persistence.xml

O arquivo `persistence.xml` está configurado para:

- Conectar ao MySQL local na porta 3306
- Usar o banco de dados `aulajpa`
- Atualizar automaticamente o esquema do banco
- Pool de conexões com 10 conexões máximas
- Suporte a variáveis de ambiente para flexibilidade

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 👨‍💻 Autor

**KaudotDev**
- GitHub: [@kaudotdev](https://github.com/kaudotdev)

---

⭐ Não esqueça de dar uma estrela se este projeto te ajudou!
