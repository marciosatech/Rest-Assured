# 🧪 Rest-Assured — Testes Automatizados de API

![Testes Automatizados - Rest Assured](https://github.com/marciosatech/Rest-Assured/actions/workflows/teste.yml/badge.svg)
![Java](https://img.shields.io/badge/Java-17-orange)
![Maven](https://img.shields.io/badge/Maven-Build-C71A36)
![Allure Report](https://img.shields.io/badge/Allure-Report-orange)

Projeto de automação de testes de API construído com **REST Assured** e **JUnit 5**, cobrindo os principais fluxos do serviço público [restful-booker](https://restful-booker.herokuapp.com/apidoc/index.html). O projeto conta com relatórios visuais via **Allure Report** e uma pipeline de CI/CD totalmente automatizada no **GitHub Actions**, que executa os testes a cada push e publica o relatório no GitHub Pages.

---

## 📖 Sobre o projeto

Este repositório tem como objetivo praticar e demonstrar boas práticas de automação de testes de API, incluindo:

- Escrita de cenários de teste com REST Assured (GET, POST) sobre a API pública Restful Booker;
- Geração de relatórios ricos e navegáveis com o Allure Report, incluindo request/response de cada chamada HTTP;
- Pipeline de CI/CD no GitHub Actions, com execução automática dos testes, geração de resumo visual dos resultados e publicação do relatório no GitHub Pages;
- Histórico de execuções (Trend) preservado entre builds, permitindo acompanhar a evolução dos testes ao longo do tempo.

---

## 🚀 Tecnologias utilizadas

| Categoria           | Tecnologia                         |
|---------------------|-------------------------------------|
| Linguagem           | Java 17                             |
| Build               | Maven                               |
| Testes              | JUnit 5                             |
| Automação de API    | REST Assured 5.3.0                  |
| Assertivas          | Hamcrest                            |
| Serialização        | Jackson Databind                    |
| Relatórios          | Allure Report                       |
| CI/CD               | GitHub Actions                      |
| Publicação          | GitHub Pages                        |

---

## 📁 Estrutura de pastas

```
Rest-Assured/
├─ 📁 .github/
│   └── 📁 workflows/
│       └── 📄 teste.yml                   # Pipeline de CI/CD (testes + relatório Allure)
├── 📁 src/
│   ├── 📁 main/
│   │   └── 📁 resources/                  # Recursos de aplicação (não utilizados nos testes)
│   └── 📁 test/
│       ├── 📁 java/
│       │   ├── 📄 BookingTest.java        # Cenários de teste da API de bookings
│       │   └── 📄 BookingEndpoint.java    # Encapsulamento de endpoints (Page Object da API)
│       └── 📁 resources/
│           ├── 📁 payloads/
│           │   └── 📄 reserva.json        # Payload utilizado no teste de criação de reserva
│           └── 📄 environment.properties  # Gerado dinamicamente pela pipeline a cada execução
├── 📁 target/                             # Artefatos de build (ignorado no Git)
├── 📁 .allure/                            # Binário do Allure baixado localmente (ignorado no Git)
├── 📄 .gitignore
└── 📄 pom.xml                             # Configuração do Maven e dependências do projeto
```

> 💡 A pasta `src/test/resources/environment.properties` é sobrescrita automaticamente pela pipeline com os dados reais do ambiente de execução (SO, versão do Java, executor). Ela não precisa ser editada manualmente.

---

## ⚙️ Como rodar localmente

### Pré-requisitos

- JDK 17 instalado
- Maven instalado 

### Executando os testes

```bash
mvn clean test
```

### Gerando e visualizando o relatório Allure

```bash
mvn allure:serve
```

Esse comando gera o relatório e abre automaticamente no navegador padrão.

---

## 🔄 Pipeline de CI/CD

A cada `push` nas branches `main`/`master`, em Pull Requests, ou manualmente via `workflow_dispatch`, o workflow [`teste.yml`](.github/workflows/teste.yml) executa as seguintes etapas:

1. **Checkout** do código-fonte;
2. Configuração do **JDK 17**;
3. Geração dinâmica do `environment.properties`, com os dados reais do runner;
4. Execução dos testes com **Maven**;
5. Publicação de um **resumo visual dos testes** (passou/falhou) no Job Summary do GitHub Actions;
6. Carregamento do **histórico** de execuções anteriores (branch `gh-pages`);
7. Geração do **relatório Allure**, já incorporando o histórico;
8. Publicação do relatório atualizado na branch `gh-pages`;
9. Publicação do **link direto do relatório** no resumo da execução.

---

### 📊 Relatório Allure publicado

O relatório mais recente fica sempre disponível em:

**[https://marciosatech.github.io/Rest-Assured/](https://marciosatech.github.io/Rest-Assured/)**

---

## 🧪 Cenários de teste cobertos

| Cenário                          | Método | Endpoint            |
|-----------------------------------|--------|----------------------|
| Buscar todas as reservas          | GET    | `/booking/`          |
| Buscar reserva por ID             | GET    | `/booking/{id}`      |
| Cadastrar nova reserva            | POST   | `/booking`           |

---

## 🤝 Contribuidores

| Nome           | GitHub                                          |
|----------------|--------------------------------------------------|
| Márcio Sá      | [@marciosatech](https://github.com/marciosatech) |

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma *issue* ou enviar um *pull request*.

---



