
# Integrantes

- Alexsandro Macedo: RM557068
- Leonardo Faria Salazar: RM557484
- Guilherme Felipe da Silva Souza: RM558282

# Eficientiza - Sistema de Gerenciamento de Motos

# Video

[Link do video](https://youtube.com/watch?v=mj4ZYCiJ8-8&feature=youtu.be) - youtube.com/watch?v=mj4ZYCiJ8-8&feature=youtu.be

## Descrição

O **Eficientiza** é um sistema de gerenciamento de motos que permite o cadastro, controle e monitoramento de motos e vagas. A aplicação permite que administradores (ADMIN) e operadores (OPERADOR) gerenciem e acompanhem as movimentações das motos no estacionamento, incluindo a visualização do histórico, a gestão das vagas e a administração dos usuários.

# Acesso ao sistema:

Para acessar o sistema pode ser usado as seguintes credenciais:

**Acesso como ADMIN**

- E-mail: admin@gmail.com

- Senha: admin

**Acesso como OPERADOR**

- E-mail: operador@gmail.com

- Senha: operador

### Imagens do sistema
<img width="1364" height="632" alt="image" src="https://github.com/user-attachments/assets/287e072a-362a-40e2-b1de-d8b5f1f6a724" />
<img width="1365" height="632" alt="image" src="https://github.com/user-attachments/assets/82cdf906-cfcf-413c-a54e-7bf720849648" />
<img width="1353" height="634" alt="image" src="https://github.com/user-attachments/assets/bd405154-677a-47b3-85b5-b7ad38d506bc" />
<img width="1352" height="638" alt="image" src="https://github.com/user-attachments/assets/a8f81465-89cc-4eea-8dbe-c4c7fbaadafc" />
<img width="1346" height="633" alt="image" src="https://github.com/user-attachments/assets/7fe0eba0-1eb8-408a-80d9-b8e5cd56b16c" />
<img width="1347" height="633" alt="image" src="https://github.com/user-attachments/assets/a93c2f7a-4e2e-4f6b-8e1d-24c53c64cb02" />







### Funcionalidades:

- **Cadastro de Motos**: Adicionar, editar e excluir motos.
- **Cadastro e Gestão de Vagas**: Monitoramento de vagas, status e a moto associada.
- **Histórico de Movimentações**: Acompanhamento do histórico de entrada e saída das motos.
- **Gestão de Usuários**: Administradores podem gerenciar usuários, atribuindo roles como ADMIN ou OPERADOR.
- **Login e Autenticação**: Sistema de autenticação baseado em **Spring Security**, com validação de senha e roles.

## Tecnologias Utilizadas

- **Spring Boot 3.x**
- **Spring Security** (para autenticação e autorização)
- **Thymeleaf** (para renderização de templates HTML)
- **Spring Data JPA** (para interação com o banco de dados)
- **H2 Database** (ou outro banco de dados configurável, como MySQL ou PostgreSQL)
- **Tailwind CSS** (para a estilização da interface)

## Estrutura do Projeto

A arquitetura do projeto segue o padrão **MVC** (Model-View-Controller), onde a lógica de negócios é separada da apresentação, e a interação com o banco de dados é feita por meio de **Repositories**.

### **Models**

As **models** representam as entidades do sistema e são responsáveis por mapear as tabelas do banco de dados.

- **`Usuario`**: Representa os usuários do sistema com os campos `id`, `nome`, `email`, `senha` e `tipo` (admin ou operador).
- **`Moto`**: Representa as motos, com informações como `placa`, `modelo`, `status`, etc.
- **`Vaga`**: Representa as vagas de estacionamento, com `id`, `status` de ocupação e a `motoId` associada.
- **`HistoricoMoto`**: Representa o histórico de movimentações das motos, incluindo a data de entrada e saída da moto.

### **Services**

Os **services** contêm a lógica de negócios e são responsáveis pela manipulação dos dados da aplicação.

- **`UsuarioService`**: Responsável por autenticar e gerenciar os usuários.
- **`MotoService`**: Manipula as operações de moto (adicionar, editar, excluir).
- **`VagaService`**: Realiza operações sobre as vagas de estacionamento.
- **`HistoricoMotoService`**: Registra e manipula as movimentações das motos.

### **Controllers**

Os **controllers** são responsáveis por mapear as requisições HTTP e interagir com os services para fornecer os dados corretos para as views.

- **`UsuarioController`**: Controla a página de login e a gestão de usuários.
- **`MotoController`**: Gerencia a listagem e os formulários para o cadastro de motos.
- **`VagaController`**: Gerencia a listagem e o controle de vagas.
- **`HistoricoMotoController`**: Controla o histórico de movimentações das motos.

### **Segurança**

A segurança é gerenciada pelo **Spring Security**. Ele utiliza autenticação baseada em **usuário e senha** com dois tipos de roles:
- **ADMIN**: Pode acessar todas as funcionalidades do sistema.
- **OPERADOR**: Tem acesso restrito, podendo visualizar e editar motos e vagas, mas não pode acessar páginas restritas como o gerenciamento de usuários.

### **Estrutura de Banco de Dados**

A aplicação utiliza um banco de dados relacional, e a estrutura de tabelas é composta por:

- **tb_mtt_usuario_c3_java**: Tabela de usuários, contendo informações como nome, e-mail, senha e tipo de usuário.
- **tb_mtt_moto_c3_java**: Tabela que armazena informações sobre as motos, como placa e modelo.
- **tb_mtt_vaga_c3_java**: Tabela de vagas de estacionamento, com o status de ocupação e a referência à moto associada.
- **tb_mtt_historico_moto_c3_java**: Tabela que registra o histórico de movimentações das motos no estacionamento.

## Instalação e Execução

### Pré-requisitos

Antes de executar o projeto, você precisará ter as seguintes ferramentas instaladas:

- **Java 17** ou superior
- **Maven** ou **Gradle** para gerenciar dependências
- **Banco de Dados** (H2, MySQL ou PostgreSQL)

### Passo 1: Clone o repositório

```bash
git clone https://github.com/seu-repositorio/eficientiza.git
```

### Passo 2: Navegue até o diretório do projeto

```bash
cd eficientiza
```

### Passo 3: Instalar as dependências e compilar o projeto

Se estiver usando **Maven**:

```bash
mvn clean install
```

Se estiver usando **Gradle**:

```bash
gradle build
```

### Passo 4: Configuração do banco de dados

O **Eficientiza** já vem configurado para usar o **H2 Database** para desenvolvimento, mas você pode alterar para outro banco de dados no arquivo **`application.properties`**.

Exemplo para usar **MySQL**:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/eficientiza
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```

### Passo 5: Executar a aplicação

Para rodar a aplicação, execute o comando:

Se estiver usando **Maven**:

```bash
mvn spring-boot:run
```

Se estiver usando **Gradle**:

```bash
gradle bootRun
```

### Passo 6: Acessando a aplicação

A aplicação estará disponível em **http://localhost:8080**. Você pode acessar as seguintes URLs:

- **`/login`**: Página de login
- **`/home`**: Página inicial após login
- **`/motos`**: Lista de motos
- **`/vagas`**: Lista de vagas
- **`/usuarios`**: Gestão de usuários (somente para ADMIN)
- **`/historico-motos`**: Gestão de historico (somente para ADMIN)

### Estrutura de Arquivos

```plaintext
src/
├── main/
│   ├── java/
│   │   └── br/com/fiap/eficientiza_challenge_03/
│   │       ├── controller/  # Controllers
│   │       ├── model/       # Entidades (Models)
│   │       ├── repository/  # Repositórios JPA
│   │       ├── service/     # Services
│   │       └── config/      # Configurações do Spring Security
│   └── resources/
│       ├── db.migration/    # Versionamento do banco de dados com Flyway
│       ├── templates/       # Páginas Thymeleaf
│       ├── application.properties  # Configurações do banco de dados
│       └── static/          # Arquivos estáticos (CSS, JS, Imagens)
└── test/                   # Testes unitários e integração
```

## Procedures

## 🧩 1. `prc_listar_ocupacoes_json`

### 📝 Descrição
Gera um **array JSON** contendo todas as ocupações registradas no sistema – incluindo informações de estações, vagas, motos e usuários.  
A procedure monta manualmente a estrutura JSON em CLOB e retorna pelo parâmetro de saída `p_json_out`.

### 🧠 Estrutura
```sql
CREATE OR REPLACE PROCEDURE prc_listar_ocupacoes_json(
    p_estacao_id     IN NUMBER,
    p_somente_ativas IN CHAR,
    p_limit          IN PLS_INTEGER,
    p_json_out       OUT CLOB
)
```

### 📤 Exemplo de Saída
```json
[{
  "id_ocupacao": 3,
  "dt_entrada": "2025-09-20T10:30:00",
  "dt_saida": "",
  "id_vaga": 3,
  "ds_vaga": "V03",
  "id_estacao": 1,
  "nm_estacao": "Estacao X01",
  "id_moto": 3,
  "ds_placa": "AAA1B03",
  "nm_modelo": "Modelo 03",
  "id_usuario": 3,
  "nm_usuario": "Usuario 03"
}]
```

### ⚡ Exemplo de Execução
```sql
DECLARE
  v_json CLOB;
BEGIN
  prc_listar_ocupacoes_json(
    p_estacao_id     => NULL,
    p_somente_ativas => 'S',
    p_limit          => 10,
    p_json_out       => v_json
  );
  DBMS_OUTPUT.PUT_LINE(v_json);
END;
```

### 💻 Consumo no Java
A aplicação consome esta procedure através do **OcupacaoSpRepository** e **OcupacaoService**.

```java
String json = ocupacaoSpRepository.listarOcupacoesJson(estacaoId, somenteAtivas, limit);
List<OcupacaoDto> lista = objectMapper.readValue(json, new TypeReference<>() {});
```

---

## 📊 2. `prc_resumo_ocupacao_minutos`

### 📝 Descrição
Produz um **resumo agregado de minutos ocupados** por combinação de **(Estação, Vaga)**.  
Realiza soma manual dos tempos de entrada/saída das ocupações e exibe o resultado via `DBMS_OUTPUT`.

### 🧠 Estrutura
```sql
CREATE OR REPLACE PROCEDURE prc_resumo_ocupacao_minutos IS
  CURSOR c_fato IS
    SELECT
      e.id_estacao      AS cat1_estacao,
      v.id_vaga         AS cat2_vaga,
      (NVL(ov.dt_saida, SYSDATE) - ov.dt_entrada) * 24 * 60 AS minutos
    FROM tb_mtt_ocupacao_vaga ov
    JOIN tb_mtt_vaga v    ON v.id_vaga = ov.id_vaga
    JOIN tb_mtt_estacao e ON e.id_estacao = v.id_estacao
    ORDER BY e.id_estacao, v.id_vaga;
BEGIN
  DBMS_OUTPUT.PUT_LINE('CAT1_ESTACAO | CAT2_VAGA | MINUTOS');
  FOR r IN c_fato LOOP
    DBMS_OUTPUT.PUT_LINE(r.cat1_estacao || ' | ' || r.cat2_vaga || ' | ' || TO_CHAR(ROUND(NVL(r.minutos,0),2)));
  END LOOP;
EXCEPTION
  WHEN NO_DATA_FOUND THEN DBMS_OUTPUT.PUT_LINE('Sem dados suficientes.');
  WHEN VALUE_ERROR THEN DBMS_OUTPUT.PUT_LINE('Erro de conversão/valor.');
  WHEN OTHERS THEN DBMS_OUTPUT.PUT_LINE('Erro inesperado: '||SQLERRM);
END;
```

### 📤 Exemplo de Saída
```
CAT1_ESTACAO | CAT2_VAGA | MINUTOS
1 | 3 | 68284.22
1 | 4 | 25912.89
2 | 1 | 1500.50
```

### 💻 Consumo no Java
O `ResumoOcupacaoRepository` executa a procedure via JDBC e lê as linhas do `DBMS_OUTPUT`.

```java
try (CallableStatement cs = con.prepareCall("{call prc_resumo_ocupacao_minutos}")) {
    cs.execute();
}
```

Cada linha é mapeada para o DTO:
```java
public record LinhaResumo(Integer estacao, Integer vaga, BigDecimal minutos) {}
```

---

## 🧭 Resumo Geral

| Procedure | Tipo de Saída | Uso Principal | Consumo Java | Exibição |
|------------|----------------|----------------|----------------|------------|
| `prc_listar_ocupacoes_json` | JSON (CLOB) | Listar ocupações detalhadas | `OcupacaoSpRepository` + `OcupacaoService` | Thymeleaf – Listar Ocupações |
| `prc_resumo_ocupacao_minutos` | DBMS_OUTPUT | Resumo por estação/vaga | `ResumoOcupacaoRepository` + `ResumoOcupacaoService` | Thymeleaf – Resumo de Ocupações |

