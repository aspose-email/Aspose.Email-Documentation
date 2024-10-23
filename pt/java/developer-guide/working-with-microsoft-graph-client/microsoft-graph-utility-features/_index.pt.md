---
title: "Recursos Utilitários do Microsoft Graph"
url: /pt/java/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Criando um Projeto no Azure Active Directory Admin Center**

Um projeto deve ser criado no Azure Active Directory admin center para um usuário com conta MS Office.
### **Passos para Criar um Projeto no Azure Active Directory Admin Center**

Segue um tutorial passo a passo para criar um projeto no Azure Active Directory admin center.

#### 1. Acesse o Azure Active Directory e faça login usando suas credenciais do MS Office.

**Link do Azure Active Directory** - <https://aad.portal.azure.com/>

#### 2. Crie um Aplicativo Azure AD em seu locatário.

No painel à esquerda, clique no rótulo **Azure Active Directory**. Isso abrirá o painel do Azure Active Directory. Nessa tela, você verá um rótulo **Registros de aplicativos**. Este é o ponto de partida para registrar um Aplicativo Azure AD. Este painel permitirá que você crie um novo aplicativo para o Azure AD.

Clique no botão **Novo registro** para criar um novo aplicativo.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Agora você verá o painel de registro do novo aplicativo.

- **Nome** Este será o nome do seu aplicativo.
- **Tipos de contas suportadas** Esta seção restringirá o acesso.

Clique no botão **Registrar**.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Você deve ver o painel de aplicativos recém-registrados.

- **ID do aplicativo (client)** O id do seu aplicativo.
- **ID do diretório (tenant)** O id do locatário do Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Permissões de autorização para a API do Microsoft Graph.

Clique no rótulo **Permissões de API**.

A Azure já lhe concedeu permissões delegadas **User.Read** para seu aplicativo. Esta permissão nos permitirá ler informações do usuário de um usuário logado. Estas são permissões da API do Microsoft Graph, por outro lado, podemos chamá-las de **Escopos**.

A lista completa de escopos para a API do Microsoft Graph - <https://docs.microsoft.com/en-us/graph/permissions-reference>.

Clique no botão **+ Adicionar uma permissão** e selecione **Microsoft Graph**.

Clique em **Permissões delegadas**. Agora você verá uma lista de permissões disponíveis para a API do Microsoft Graph.

Selecione as permissões necessárias, clique no botão **Adicionar permissões**.

Clique no botão **Conceder consentimento do administrador**.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Permitir fluxos de clientes públicos.

Especifica se o aplicativo é um cliente público. Apropriado para aplicativos que usam fluxos de concessão de token que não utilizam um URI de redirecionamento.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Crie uma chave para o aplicativo

![todo:image_alt_text](microsoft-graph-utility-features_5.png)

## **Classes Auxiliares**

As seguintes classes auxiliares são necessárias para executar os códigos nesta seção. Essas classes são apenas para simplificação da demonstração.

### **Classe AzureROPCTokenProvider**

Uma instância da classe [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) manipula a construção de requisições, enviando-as para a API do Microsoft Graph e processando as respostas. Para criar uma nova instância desta classe, você precisa fornecer uma instância de [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), que pode autenticar requisições para o Microsoft Graph.

~~~Java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.OutputStream;
import java.io.UnsupportedEncodingException;
import java.net.HttpURLConnection;
import java.net.URL;
import java.net.URLDecoder;
import java.net.URLEncoder;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

/**
 * <p>
 * Azure resource owner password credential (ROPC) token provider
 * https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth-ropc
 * https://docs.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-authenticate-an-ews-application-by-using-oauth
 * https://portal.azure.com
 * https://developer.microsoft.com/en-us/graph/graph-explorer/#
 * token parser https://jwt.io
 * </p>
 */
class AzureROPCTokenProvider implements ITokenProvider {

    private static final String GRANT_TYPE = "password";

    private final String clientId;
    private final String clientSecret;
    private final String userName;
    private final String password;
    private final String tenant;
    private final String scope;

    private OAuthToken token;

    public AzureROPCTokenProvider(String tenant, String clientId, String clientSecret,
                                  String userName, String password, String[] scopeAr) {
        this.tenant = tenant;
        this.clientId = clientId;
        this.clientSecret = clientSecret;
        this.userName = userName;
        this.password = password;
        this.scope = joinToStr(scopeAr, " ");
    }

    public synchronized OAuthToken getAccessToken(boolean ignoreExistingToken) {
        if (this.token != null && !this.token.getExpired() && !ignoreExistingToken)
            return this.token;
        token = null;

        Map<String, String> tokenArgs = geToken();

        java.util.Calendar c = java.util.Calendar.getInstance();
        c.add(java.util.Calendar.SECOND, Integer.parseInt(tokenArgs.get("expires_in")));
        token = new OAuthToken(tokenArgs.get("access_token"), TokenType.AccessToken, c.getTime());
        return token;
    }

    public final OAuthToken getAccessToken() {
        return getAccessToken(false);
    }

    public void dispose() {
    }

    private String getEncodedParameters() {
        return "client_id=" + urlEncode(clientId) + "&scope=" + urlEncode(scope) + "&username=" + urlEncode(userName)
                + "&password=" + urlEncode(password) + "&grant_type="
                + urlEncode(GRANT_TYPE);
    }

    private String getUri() {
        if (tenant == null || tenant.trim().isEmpty())
            return "https://login.microsoftonline.com/common/oauth2/v2.0/token";
        else
            return "https://login.microsoftonline.com/" + tenant + "/oauth2/v2.0/token";
    }

    private Map<String, String> geToken() {
        try {
            HttpURLConnection connection = (HttpURLConnection) new URL(getUri()).openConnection();
            connection.setRequestMethod("POST");

            byte[] requestData = getEncodedParameters().getBytes(StandardCharsets.UTF_8);

            connection.setUseCaches(false);
            connection.setDoInput(true);
            connection.setDoOutput(true);
            connection.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");
            connection.setRequestProperty("Content-Length", "" + requestData.length);

            final OutputStream st = connection.getOutputStream();
            try {
                st.write(requestData, 0, requestData.length);
            } finally {
                st.flush();
                st.close();
            }

            connection.connect();

            if (connection.getResponseCode() >= HttpURLConnection.HTTP_BAD_REQUEST) {
                throw new IllegalAccessError("Operation failed: " + connection.getResponseCode() + "/" +
                        connection.getResponseMessage() + "\r\nDetails:\r\n{2}"
                        + readInputStream(connection.getErrorStream()));
            }

            String responseText = readInputStream(connection.getInputStream());

            Map<String, String> result = new HashMap<>();
            String[] fromJsonToKeyValue = responseText.replace("{", "").replace("}", "")
                    .replace("\"", "").replace("\r", "")
                    .replace("\n", "").split(",");
            for (String keyValue : fromJsonToKeyValue) {
                String[] pair = keyValue.split(":");
                String name = pair[0].trim().toLowerCase();
                String value = urlDecode(pair[1].trim());
                result.put(name, value);
            }

            return result;
        } catch (IOException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String urlEncode(String value) {
        try {
            return URLEncoder.encode(value, StandardCharsets.UTF_8.toString());
        } catch (UnsupportedEncodingException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String urlDecode(String value) {
        try {
            return URLDecoder.decode(value, StandardCharsets.UTF_8.toString());
        } catch (UnsupportedEncodingException e) {
            throw new IllegalAccessError(e.getMessage());
        }
    }

    static String readInputStream(InputStream is) {
        if (is == null)
            return "";

        BufferedReader reader = new BufferedReader(new InputStreamReader(is));
        StringBuilder result = new StringBuilder();
        String line;
        try {
            while ((line = reader.readLine()) != null) {
                result.append(line);
            }
        } catch (IOException e) {
            // ignore
        }
        return result.toString();
    }

    static String joinToStr(String[] arr, String sep) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < arr.length; i++) {
            if (i > 0)
                sb.append(sep);
            sb.append(arr[i]);
        }
        return sb.toString();
    }
}
~~~