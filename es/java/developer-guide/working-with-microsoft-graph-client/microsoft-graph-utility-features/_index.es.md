---
title: "Características de Microsoft Graph Utility"
url: /es/java/microsoft-graph-utility-features/
weight: 10
type: docs
---


## **Creación de un proyecto en el Centro de administración de Azure Active Directory**

Se va a crear un proyecto en el centro de administración de Azure Active Directory para un usuario que tenga una cuenta de MS Office.
### **Pasos para crear un proyecto en el Centro de administración de Azure Active Directory**

A continuación se muestra un tutorial paso a paso para crear un proyecto en el centro de administración de Azure Active Directory.

#### 1. Vaya a Azure Active Directory e inicie sesión con sus credenciales de MS Office.

**Azure Active Directory** Enlace - <https://aad.portal.azure.com/>

#### 2. Cree una aplicación Azure AD en su inquilino.

En el panel lateral izquierdo, haga clic en la etiqueta **Azure Active Directory**. Esto abrirá la hoja para Azure Active Directory. En esa pantalla debería aparecer una etiqueta **Registros de aplicaciones**. Este es el punto de partida para registrar una aplicación Azure AD. Esta hoja le permitirá crear una nueva aplicación para Azure AD.

Haga clic en el botón **Nuevo registro** para crear una nueva aplicación.

![todo:image_alt_text](microsoft-graph-utility-features_1.png)

#### 3. Ahora verá la nueva hoja de registro de aplicaciones.

- **Name** Este será el nombre de su solicitud.
- **Tipos de cuentas compatibles** Esta sección restringirá el acceso.

Click **Register** button.

![todo:image_alt_text](microsoft-graph-utility-features_2.png)

#### 4. Debería ver la hoja de aplicaciones recién registradas.

- **ID de aplicación (cliente)** El identificador de su solicitud.
- **ID de directorio (inquilino)** El identificador de inquilino de Azure AD.

![todo:image_alt_text](microsoft-graph-utility-features_6.png)

#### 5. Permitir permisos para la API de Microsoft Graph.

Haga clic en el **Permisos de API** label.

Azure ya le ha dado **User.Read** permisos delegados para su aplicación. Este permiso nos permitirá leer la información de usuario de un usuario que haya iniciado sesión. Estos son los permisos de la API de Microsoft Graph, por otro lado, podemos llamarlos como **Scopes**.

La lista completa de ámbitos de la API de Microsoft Graph - <https://docs.microsoft.com/en-us/graph/permissions-reference>.

Haga clic en **+ Añadir un permiso** botón y selección **Microsoft Graph**.

Haga clic en **Permisos delegados**. Ahora puede ver una lista de los permisos disponibles para la API de Microsoft Graph.

Seleccione los permisos necesarios y haga clic **Añadir permisos** button.

Click **Otorgar el consentimiento del administrador** button.

![todo:image_alt_text](microsoft-graph-utility-features_3.png)

#### 6. Permita los flujos de clientes públicos.

Especifica si la aplicación es un cliente público. Apropiado para aplicaciones que utilizan flujos de concesión de tokens que no utilizan un URI de redireccionamiento.

![todo:image_alt_text](microsoft-graph-utility-features_4.png)

#### 7. Crea una clave para la aplicación

![todo:image_alt_text](microsoft-graph-utility-features_5.png)

## **Clases de ayuda**

Se requieren las siguientes clases auxiliares para ejecutar los códigos de esta sección. Estas clases son solo para simplificar la demostración.

### **Clase AzureRopcTokenProvider**

Una instancia del [IGraphClient](https://apireference.aspose.com/email/java/com.aspose.email/IGraphClient) La clase gestiona la creación de solicitudes, las envía a la API de Microsoft Graph y procesa las respuestas. Para crear una nueva instancia de esta clase, debes proporcionar una instancia de [ITokenProvider](https://apireference.aspose.com/email/java/com.aspose.email/ITokenProvider), que puede autenticar las solicitudes en Microsoft Graph.

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
