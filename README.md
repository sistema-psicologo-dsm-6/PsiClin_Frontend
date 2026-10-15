# PsiClin - Frontend

Aplicação multiplataforma para apoiar o cadastro e a organização de informações de uma clínica de psicologia. A interface é construída com Kotlin e Compose Multiplatform, compartilhando código entre Android, navegador e desktop.
## Funcionalidades

- Cadastro de pacientes.
- Cadastro de horários disponíveis.
## Identificação

- **Projeto:** PsiClin
- **Grupo no GitHub:** sistema-psicologo-dsm-6 (confirmar a denominação oficial do grupo)

- **Repositório do frontend:** [PsiClin_Frontend](https://github.com/sistema-psicologo-dsm-6/PsiClin_Frontend)
- **Repositório do backend:** [PsiClin-Backend](https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend)

## Integrantes e responsabilidades

Os nomes abaixo são as identificações registradas nos commits do frontend. As responsabilidades listadas correspondem aos formulários cuja autoria aparece no histórico Git; confirmem os nomes completos e a divisão oficial do grupo para a entrega.

| Integrante (identificação Git) | Entidades/formulários do frontend |
| --- | --- |
| Eduardajs3 | Paciente e Horário Disponível |
| Dalvinha75 | Prontuário e Sala de Atendimento |

## Sobre o projeto

O PsiClin é um sistema de apoio à gestão de atendimentos psicológicos. A solução reúne cadastros e informações da rotina clínica para reduzir a dependência de registros dispersos e padronizar o gerenciamento de pacientes, profissionais, horários, atendimentos e prontuários.

O projeto é dividido em dois repositórios. O frontend deste repositório oferece uma interface multiplataforma; o backend separado fornece uma API REST e persiste os dados em MariaDB. No frontend atual, o menu já permite acessar os formulários de paciente e horário disponível. Os formulários de prontuário e sala de atendimento também existem no código compartilhado, mas ainda não estão ligados ao menu principal.

## Tecnologias

**Frontend:** Kotlin 2.4.20, Compose Multiplatform 1.12.1, Material 3, Gradle Kotlin DSL e JDK 21. Alvos: Android, navegador (WebAssembly ou JavaScript) e Desktop (JVM).

**Backend:** Kotlin 2.3.21, Spring Boot 4.1.1, Spring Web MVC, Spring Data JPA, Jakarta Bean Validation, MariaDB, Gradle Wrapper e JDK 25.

## Arquitetura e organização

### Frontend

O frontend compartilha interface entre plataformas. O código atual não estabelece uma divisão formal entre camadas de apresentação, domínio e dados.

| Área | Diretório | Responsabilidade |
| --- | --- | --- |
| Interface e navegação compartilhadas | `shared/src/commonMain/kotlin/edu/front/psi/clin/` | Telas Compose, menu e formulários |
| Modelos | `shared/src/commonMain/kotlin/edu/front/psi/clin/model/` | Modelos de domínio usados pela interface |
| Android | `androidApp/` e `shared/src/androidMain/` | Configuração e integração Android |
| Web | `webApp/`, `shared/src/wasmJsMain/` e `shared/src/jsMain/` | Aplicação para navegador |
| Desktop | `desktopApp/` e `shared/src/jvmMain/` | Aplicação Desktop para JVM |

### Backend

O backend está no [repositório PsiClin-Backend](https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend). Suas camadas ficam em `src/main/kotlin/com/edu/psiclinbe/`:

| Camada | Diretório | Responsabilidade |
| --- | --- | --- |
| API REST | `controller/` | Endpoints HTTP |
| Contratos da API | `dto/` | Dados de entrada e saída, incluindo validações |
| Conversão de dados | `mapper/` | Conversão entre DTOs e entidades |
| Domínio e persistência | `model/` | Entidades JPA e enums |
| Acesso a dados | `repository/` | Repositórios Spring Data JPA |
| Regras de negócio | `service/` | Serviços da aplicação |

Os recursos de configuração ficam em `src/main/resources/`; os testes, em `src/test/kotlin/`.

## Instalação e execução

### Frontend

Requer JDK 21. Execute os comandos na raiz deste repositório. No Windows, use PowerShell; em Linux ou macOS, use os comandos indicados para Bash.

Para iniciar a versão WebAssembly:

```powershell
.\gradlew.bat :webApp:wasmJsBrowserDevelopmentRun
```

```bash
./gradlew :webApp:wasmJsBrowserDevelopmentRun
```

O Gradle inicia o servidor de desenvolvimento e abre o navegador. Acesse o endereço local informado no terminal, normalmente `http://localhost:8080`. Para usar JavaScript em vez de WebAssembly, execute `:webApp:jsBrowserDevelopmentRun`.

Para iniciar a versão Desktop:

```powershell
.\gradlew.bat :desktopApp:run
```

```bash
./gradlew :desktopApp:run
```

Para compilar o APK Android de depuração:

```powershell
.\gradlew.bat :androidApp:assembleDebug
```

O arquivo é gerado em `androidApp/build/outputs/apk/debug/`. Para instalar e abrir o app, use o Android Studio com um emulador ou dispositivo conectado.

### Backend

Requer JDK 25 e MariaDB. As instruções completas estão no [README do backend](https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend#readme). Resumo para Windows PowerShell, a partir da raiz do repositório backend:

1. Inicie um banco MariaDB. Com Docker, por exemplo:

   ```powershell
   docker run --name psiclinbe-mariadb --restart unless-stopped -e MARIADB_ROOT_PASSWORD=change-me -e MARIADB_DATABASE=psiclinbe -p 3307:3306 -v psiclinbe-mariadb-data:/var/lib/mysql -d mariadb:11.4
   ```

2. Crie o arquivo local de configuração e ajuste as credenciais conforme seu banco:

   ```powershell
   Copy-Item .env.example .env
   ```

3. Inicie a API:

   ```powershell
   .\gradlew.bat bootRun
   ```

A API escuta por padrão em `http://localhost:8080`. O frontend Web também pode usar a porta 8080; para executá-los simultaneamente, configure outra porta para o backend usando `SERVER_PORT` no `.env`.

## Testes

Na raiz do frontend, execute os testes desejados:

```powershell
.\gradlew.bat :shared:testAndroidHostTest
.\gradlew.bat :shared:jvmTest
.\gradlew.bat :shared:wasmJsTest
.\gradlew.bat :shared:jsTest
```

Os testes do backend podem ser executados, na raiz do repositório backend, com `gradlew.bat test`; consulte o README do backend para os requisitos de conexão com MariaDB.