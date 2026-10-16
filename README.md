# PsiClin_Frontend

## Identificação do projeto

- **Projeto:** PsiClin_Frontend — protótipo de interface para uma clínica de psicologia.
- **Grupo:** Agostinho Benigno Monteiro Gutierrez, Afonso Rocha Sprocatti, Eduarda Josileide da Silva, Lindalva Carlos da Silva, Westes Mesquita da Silva Oliveira.
- **Repositório do backend:** https://github.com/sistema-psicologo-dsm-6/PsiClin-Backend
- **Repositório do frontend:** [https://github.com/sistema-psicologo-dsm-6/PsiClinFrontend](https://github.com/sistema-psicologo-dsm-6/PsiClin_Frontend.git)
  
## Integrantes e entidades


| Integrante (GitHub) | Nomes dos usuários | Entidades |
| --- | --- | --- |
| agostinho58| Agostinho Benigno Monteiro Gutierrez | Agenda, BloqueioAgenda |
| Dalvinha75 |  Lindalva Carlos da Silva | Prontuario, SalaAtendimento |
| Eduardajs3 | Eduarda Josileide da Silva | Paciente, HorarioDisponivel, Pagamento |
| Hush9K |Afonso Rocha Sprocatti | Funcionario, Convenio, EvolucaoClinica |
| westes.mso | Westes Mesquita da Silva Oliveira | Psicologo, Recepcionista, TipoAtendimento|

### Entidades do projeto

O projeto contém modelos para:

- Agenda
- Bloqueio de agenda
- Convênio
- Evolução clínica
- Funcionário
- Horário disponível
- Paciente
- Pagamento
- Prontuário
- Psicólogo
- Recepcionista
- Sala de atendimento
- Tipo de atendimento

Cada modelo está em `shared/src/commonMain/kotlin/edu/front/psi/clin/model/`, e os formulários correspondentes estão no pacote `edu.front.psi.clin`, em `shared/src/commonMain/kotlin/edu/front/psi/clin/`.

## Descrição da aplicação

O FrontPsiClinic é um protótipo multiplataforma de interface para organizar cadastros e informações de uma clínica de psicologia. A aplicação reúne formulários de pacientes, profissionais, agenda, prontuários, pagamentos e outros dados relacionados ao atendimento.

A centralização dessas telas busca facilitar a visualização das áreas funcionais da clínica e demonstrar como seus dados podem ser inseridos. O projeto ainda é uma interface demonstrativa: não possui conexão com backend, banco de dados ou persistência. 

## Tecnologias utilizadas

- Kotlin Multiplatform
- Compose Multiplatform
- Material 3
- Gradle 9.5.1 com Gradle Wrapper
- Android, Desktop (JVM), JavaScript e WebAssembly como alvos configurados

Versões principais configuradas em `gradle/libs.versions.toml`: Kotlin 2.4.20, Compose Multiplatform 1.12.1 e Material 3 1.12.0-alpha03.

## Arquitetura e organização

 A arquitetura existente é a do frontend multiplataforma:

| Camada/área | Implementação |
|---|---|
| Interface e navegação | `shared/src/commonMain/kotlin/edu/front/psi/clin/` — telas de formulário, menu e componentes visuais Compose |
| Modelos de domínio | `shared/src/commonMain/kotlin/edu/front/psi/clin/model/` — entidades Kotlin compartilhadas |
| Recursos compartilhados | `shared/src/commonMain/composeResources/` |
| Inicialização Android | `androidApp/src/main/` |
| Inicialização Desktop | `desktopApp/src/main/kotlin/` |
| Inicialização Web | `webApp/src/webMain/kotlin/` e `webApp/src/webMain/resources/` |

Os formulários e modelos ficam no módulo `shared` para serem reutilizados pelos alvos Android, Desktop e Web. 

## Requisitos

- Git para clonar o repositório remoto.
- JDK em uma versão compatível com a configuração do projeto.
- Android Studio com Android SDK para executar no Android.
- Navegador compatível para executar as versões Web.

O Gradle Wrapper baixa a versão necessária do Gradle na primeira execução. A compilação também pode baixar dependências, portanto é necessário acesso à internet na configuração inicial.

## Instalação

Clone o repositório remoto do grupo:

```powershell
git clone https://github.com/sistema-psicologo-dsm-6/PsiClin_Frontend.git
cd PsiClin_Frontend
```

Abra a pasta do projeto no VS Code, Android Studio ou use o terminal com o Gradle Wrapper incluído.

## Execução

Execute os comandos a partir da raiz do projeto. No Windows, use `.\gradlew.bat`; no macOS/Linux, use `./gradlew`.

### Desktop

```powershell
.\gradlew.bat :desktopApp:run
```

O aplicativo é aberto em uma janela Desktop.

### WebAssembly

```powershell
.\gradlew.bat :webApp:wasmJsBrowserDevelopmentRun
```

O Gradle inicia o servidor de desenvolvimento e abre a aplicação no navegador. O endereço local é informado no terminal.

### JavaScript

```powershell
.\gradlew.bat :webApp:jsBrowserDevelopmentRun
```

### Android

Conecte um dispositivo Android ou inicie um emulador configurado no Android Studio. Para gerar o APK de depuração:

```powershell
.\gradlew.bat :androidApp:assembleDebug
```

O APK é gerado em `androidApp/build/outputs/apk/debug/`. Também é possível abrir o projeto no Android Studio, selecionar a configuração Android e executar no dispositivo ou emulador.

## Acesso à aplicação

- **Desktop:** a aplicação é acessada na janela aberta pelo comando `:desktopApp:run`.
- **Web:** acesse no navegador o endereço local exibido pelo Gradle ao iniciar o servidor de desenvolvimento.
- **Android:** instale e abra o APK gerado ou execute a aplicação diretamente pelo Android Studio em um dispositivo/emulador.


