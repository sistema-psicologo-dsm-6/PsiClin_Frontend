# PsiClin - Frontend

Aplicação multiplataforma para apoiar a gestão de uma clínica de psicologia. A interface foi desenvolvida com Kotlin e Compose Multiplatform, compartilhando a maior parte do código entre Android, navegador e desktop.

## Sobre o projeto

O PsiClin reúne telas para cadastrar e organizar informações da rotina de uma clínica, como pacientes, profissionais, agenda, atendimentos e prontuários. O projeto é dividido em dois repositórios:

- **Frontend:** interface multiplataforma neste repositório.
- **Backend:** API REST e persistência de dados no [repositório PsiClin-Backend](https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend).

No estado atual, o frontend apresenta formulários e navegação local entre as telas. Os formulários ainda não estão integrados à API nem persistem os dados; as informações inseridas não são mantidas após o encerramento da aplicação.

## Integrantes e participação

O grupo do projeto é **sistema-psicologo-dsm-6**. A tabela registra as contribuições identificadas no histórico de commits do frontend:

| Integrante | Usuário no GitHub | Participação no frontend |
| --- | --- | --- |
| Agostinho Benigno Monteiro Gutierrez | [agostinho58](https://github.com/agostinho58) | Formulários de agenda e bloqueio de agenda. |
| Afonso Rocha Sprocatti | [Hush9K](https://github.com/Hush9K) | Formulários de convênio, evolução clínica e funcionário. |
| Eduarda Josileide da Silva | [Eduardajs3](https://github.com/Eduardajs3) | Formulários de paciente e horário disponível. |
| Lindalva Carlos da Silva | [Dalvinha75](https://github.com/Dalvinha75) | Formulários de prontuário e sala de atendimento; integração dos formulários ao menu e padronização de botões. |
| Westes Mesquita da Silva Oliveira | [karyanpierrot](https://github.com/karyanpierrot) | Formulários de psicólogo, recepcionista e tipo de atendimento |

## Funcionalidades disponíveis

O menu principal permite abrir os formulários de:

- Paciente
- Funcionário
- Convênio
- Horário disponível
- Agenda
- Bloqueio de agenda
- Psicólogo e recepcionista
- Tipo de atendimento
- Prontuário e sala de atendimento
- Evolução clínica

Essas telas são a interface atual do projeto. O cadastro definitivo, a autenticação e a comunicação com o backend ainda não estão disponíveis no frontend.

## Tecnologias

- Kotlin 2.4.20
- Compose Multiplatform 1.12.1 e Material 3
- Gradle 9.5.1, executado pelo Gradle Wrapper
- JDK 21
- Android, navegador (WebAssembly ou JavaScript) e desktop (JVM)

## Estrutura do projeto

| Módulo ou diretório | Responsabilidade |
| --- | --- |
| `shared/src/commonMain/kotlin/edu/front/psi/clin/` | Interface Compose compartilhada, navegação e formulários. |
| `shared/src/commonMain/kotlin/edu/front/psi/clin/model/` | Modelos de dados usados pelas telas. |
| `shared/src/androidMain/`, `shared/src/jsMain/`, `shared/src/wasmJsMain/` e `shared/src/jvmMain/` | Implementações específicas de cada plataforma. |
| `androidApp/` | Aplicativo Android. |
| `webApp/` | Aplicação executável no navegador. |
| `desktopApp/` | Aplicação desktop para JVM. |

## Pré-requisitos

- JDK 21 instalado e disponível no `PATH`.
- Navegador compatível para executar a versão Web.
- Para compilar ou executar no Android, Android SDK e um emulador ou dispositivo. O Android Studio pode ser usado para configurar o SDK e iniciar o aplicativo.

O Gradle Wrapper incluído no repositório baixa e utiliza a versão de Gradle configurada pelo projeto.

## Instalação e execução

Clone o repositório e entre na pasta do projeto:

```powershell
git clone https://github.com/sistema-psicologo-dsm-6/PsiClin_Frontend.git
cd PsiClin_Frontend
```

Os comandos abaixo devem ser executados na raiz do repositório.

### Navegador

Para iniciar a versão WebAssembly no Windows (PowerShell):

```powershell
.\gradlew.bat :webApp:wasmJsBrowserDevelopmentRun
```

No Linux ou macOS:

```bash
./gradlew :webApp:wasmJsBrowserDevelopmentRun
```

O Gradle inicia o servidor de desenvolvimento. Abra no navegador o endereço local indicado no terminal.

Para executar a versão JavaScript, use `:webApp:jsBrowserDevelopmentRun` no lugar de `:webApp:wasmJsBrowserDevelopmentRun`.

### Desktop

Windows (PowerShell):

```powershell
.\gradlew.bat :desktopApp:run
```

Linux ou macOS:

```bash
./gradlew :desktopApp:run
```

### Android

Com Android SDK configurado, compile o APK de depuração:

```powershell
.\gradlew.bat :androidApp:assembleDebug
```

O APK será gerado em `androidApp/build/outputs/apk/debug/`. Para executar o aplicativo, abra o projeto no Android Studio e selecione um emulador ou dispositivo conectado.

## Testes

Execute os testes da plataforma desejada a partir da raiz do projeto:

```powershell
.\gradlew.bat :shared:jvmTest
.\gradlew.bat :shared:wasmJsTest
.\gradlew.bat :shared:jsTest
.\gradlew.bat :shared:testAndroidHostTest
```

No Linux ou macOS, substitua `.\gradlew.bat` por `./gradlew`.

## Repositórios

- [PsiClin_Frontend](https://github.com/sistema-psicologo-dsm-6/PsiClin_Frontend)
- [PsiClin-Backend](https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend)
