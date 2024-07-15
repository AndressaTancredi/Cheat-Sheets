
### 📋 Documentação para Publicar um App Flutter na Google Play Store

Esta documentação cobre os passos necessários para configurar e publicar um aplicativo Flutter na Google Play Store pela primeira vez.

---

#### 1. 🛠️ Preparação do Projeto Flutter

1. **Atualizar `pubspec.yaml`**:
   - Certifique-se de que todas as dependências estejam atualizadas.
   - Defina uma versão para o seu app (`version: 1.0.0+1`).

2. **Configurar o `AndroidManifest.xml`**:
   - Abra o arquivo `android/app/src/main/AndroidManifest.xml` e atualize o atributo `package` com um nome de pacote exclusivo.
   ```xml
   <manifest xmlns:android="http://schemas.android.com/apk/res/android"
       package="com.seu.nome.unico">
       ...
   </manifest>
   ```

3. **Configurar o `build.gradle`**:
   - Abra o arquivo `android/app/build.gradle` e certifique-se de que o `applicationId` corresponda ao novo nome de pacote.
   ```groovy
   android {
       ...
       defaultConfig {
           applicationId "com.seu.nome.unico"
           ...
       }
       ...
   }
   ```

4. **Renomear Diretórios Java/Kotlin**:
   - Navegue até `android/app/src/main/java/com/example/` e renomeie o diretório `example` para corresponder ao seu novo nome de pacote (`com/seu/nome/unico`).

#### 2. 🔑 Gerar e Configurar a Keystore

1. **Criar uma Keystore**:
   - Execute o comando no terminal:
   ```bash
   keytool -genkey -v -keystore /Users/andressa/APPs/hydrateMeAndroidKeystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias hydrateMeKeystore
   ```
   - Preencha as informações solicitadas.

2. **Criar o Arquivo `key.properties`**:
   - No diretório `android` do projeto, crie um arquivo `key.properties` com o seguinte conteúdo:
   ```properties
   storePassword=android
   keyPassword=android
   keyAlias=hydrateMeKeystore
   storeFile=/Users/andressa/APPs/hydrateMeAndroidKeystore.jks
   ```

3. **Configurar o `build.gradle`**:
   - Atualize o arquivo `android/app/build.gradle` para usar a keystore configurada.
   ```groovy
   signingConfigs {
       release {
           keyAlias keyProperties['keyAlias']
           keyPassword keyProperties['keyPassword']
           storeFile file(keyProperties['storeFile'])
           storePassword keyProperties['storePassword']
       }
   }

   buildTypes {
       release {
           signingConfig signingConfigs.release
           minifyEnabled true
           shrinkResources true
           proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
       }
   }
   ```

#### 3. 📦 Gerar o App Bundle

1. **Gerar um App Bundle**:
   - Execute o comando:
   ```bash
   flutter build appbundle --release
   ```

#### 4. 🌐 Publicar no Google Play Console

1. **Criar uma Conta de Desenvolvedor**:
   - Acesse o [Google Play Console](https://play.google.com/console) e crie uma conta de desenvolvedor.

2. **Criar um Novo Aplicativo**:
   - No Play Console, clique em "Criar aplicativo" e preencha as informações necessárias (nome, descrição, ícones, etc.).

3. **Upload do App Bundle**:
   - Na seção de "Release", faça o upload do arquivo `.aab` gerado.

4. **Preencher Informações do App**:
   - Preencha todas as informações requeridas, como classificação de conteúdo, política de privacidade, etc.

5. **Enviar para Revisão**:
   - Após preencher todas as informações e fazer o upload do app, envie o app para revisão.

#### 5. ⏳ Aguardar Aprovação

- O processo de revisão pode levar algumas horas ou dias. Você será notificado por e-mail sobre o status da sua publicação.

---

Seguindo esses passos, você deve ser capaz de configurar e publicar seu aplicativo Flutter na Google Play Store com sucesso.
