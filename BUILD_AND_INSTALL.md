# VisionAdapt — build e instalação

## 1. Build principal (recomendado / Google Play)

A configuração principal é a de lançamento:

- applicationId: `com.visionadapt.mobile`
- compileSdk: 36
- targetSdk: 36
- minSdk: 26
- AGP: 8.13.2
- Gradle: 8.13
- JDK: 17
- Google Play Billing: 9.1.0

Ela atende ao requisito de target API 36 para novos apps enviados ao Google Play a partir de 31/08/2026.

### Android Studio / terminal

Instale Android SDK Platform 36 e Build Tools 36.0.0 e execute:

```bash
gradle :app:assembleDebug
```

APK de debug esperado:

`app/build/outputs/apk/debug/app-debug.apk`

Para artefatos de lançamento:

```bash
gradle :app:assembleRelease :app:bundleRelease
```

Antes de publicar, configure assinatura de release em ambiente seguro. Não coloque senha ou keystore no repositório.

## 2. GitHub Actions

O arquivo `.github/workflows/android-build.yml` prepara JDK 17, SDK 36, Gradle 8.13, executa os testes do núcleo e gera APK/AAB. Depois de colocar o projeto num repositório, o workflow pode ser disparado manualmente em **Actions > Android build > Run workflow**.

## 3. AndroidIDE no celular

O AndroidIDE oficial foi arquivado e sua última linha declarava suporte explícito a AGP 8.2.x. Para desenvolvimento local no aparelho, se o build principal com AGP 8.13.2 não sincronizar, use temporariamente os arquivos em `androidide-compat/` conforme o README daquela pasta.

Essa configuração de compatibilidade usa API 34 e serve somente para **teste local**. Não envie esse build ao Google Play em setembro de 2026.

## Premium no debug vs release

- **Debug:** existe um teste Premium local de 7 dias apenas para permitir testar o fluxo completo antes de configurar Play Console.
- **Release:** o teste local é desativado. Premium depende de uma compra/assinatura reconhecida pelo Google Play.
- Configure o produto `visionadapt_premium_monthly` no Play Console.
- Se usar uma oferta específica, marque-a com a tag `visionadapt_default`.
- Um teste gratuito de 7 dias, se desejado comercialmente, deve ser configurado na oferta do Google Play, não no armazenamento local do app.
