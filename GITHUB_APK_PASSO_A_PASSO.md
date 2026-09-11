# VisionAdapt RC1 — gerar APK pelo GitHub

Este pacote usa GitHub Actions. Não precisa de AndroidIDE nem de computador para compilar.

## 1. Criar o repositório

1. Entre em https://github.com/new
2. Repository name: `VisionAdapt`
3. Escolha **Private** se quiser manter o código fechado.
4. Não adicione README, .gitignore ou licença nessa tela.
5. Toque em **Create repository**.

## 2. Enviar os arquivos

1. Dentro do repositório, toque em **uploading an existing file** / **Add file > Upload files**.
2. O GitHub precisa receber o CONTEÚDO desta pasta na raiz do repositório — `app`, `.github`, `tools`, `build.gradle`, `settings.gradle` etc.
3. Confirme em **Commit changes**.

> Importante: a raiz do repositório deve mostrar `app/` e `.github/` diretamente. Não deixe tudo dentro de uma pasta extra `VisionAdapt_GitHub_APK/`.

## 3. Compilar

1. Abra a aba **Actions**.
2. Se o GitHub pedir, toque em **I understand my workflows, go ahead and enable them**.
3. Abra **Build VisionAdapt APK**.
4. Toque em **Run workflow** > **Run workflow**.
5. Abra a execução que aparecer e aguarde todos os passos ficarem verdes.

## 4. Baixar o APK

1. Na página da execução concluída, desça até **Artifacts**.
2. Toque em **VisionAdapt-RC1-APK**.
3. O GitHub baixa um ZIP.
4. Extraia esse ZIP no Samsung.
5. Dentro estará `app-debug.apk`.
6. Toque no APK e permita **Instalar apps desconhecidos** para o navegador/Meus Arquivos quando o Android solicitar.
7. Instale o VisionAdapt.

## Configuração usada

- Java 17
- Gradle 8.13
- Android Gradle Plugin 8.13.2
- compileSdk 36
- targetSdk 36
- minSdk 26
- Debug APK com Premium local de teste habilitado apenas para desenvolvimento
