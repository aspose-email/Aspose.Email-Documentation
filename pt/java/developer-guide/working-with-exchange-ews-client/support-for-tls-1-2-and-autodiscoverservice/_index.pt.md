---
title: "Suporte para TLS 1.2 e AutodiscoverService"
url: /pt/java/support-for-tls-1-2-and-autodiscoverservice/
weight: 180
type: docs
---

Aspose.Email para Java agora suporta TLS 1.2 usando a API SAAJ. O [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) fornece uma propriedade estática [useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)) que pode ser definida como **true** para usar TLS 1.2. Aspose.Email para Java também suporta [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) para TLS 1.2. Os seguintes exemplos de código demonstram o uso da API SAAJ e [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) para TLS 1.2.
## **Usar API SAAJ**
O cliente SOAP Java EE usado com o modo SAAJAPI - <https://docs.oracle.com/cd/E19651-01/817-2151-10/wsgjaxm.html>. 

O seguinte exemplo de código demonstra o uso da API SAAJ definindo a propriedade [EWSClient.useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)) como **true**.

No próximo trecho de código, o cabeçalho de autenticação básica será atribuído:

~~~Java
EWSClient.useSAAJAPI(true);
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testuser", "pw", "domain");
client.listMessages();
~~~
No próximo trecho de código, o cabeçalho de autenticação OAUTH2 será atribuído:

~~~Java
EWSClient.useSAAJAPI(true);
// token provider
/*ITokenProvider provider = new ITokenProvider() {

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        return null;
    }
};

NetworkCredential credentials = new OAuthNetworkCredential(provider);*/

// accessToken
NetworkCredential credentials = new OAuthNetworkCredential("accessToken");

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", credentials);
client.listMessages();
~~~

{{% alert color="primary" %}} 

Observe que neste modo, a API não controla o processo de autenticação NTLM.
O autenticador Java é necessário para autenticação NTLM.

{{% /alert %}} 

O trecho de código de autenticação NTLM para Java 8:

~~~Java
import java.net.Authenticator;
import java.net.PasswordAuthentication;
import java.net.URL;

static Authenticator getAuthenticator(String user, String pw, String domain) {
    final String username = domain + "\\" + user;
    final String password = pw;
    System.out.println("Novas Credenciais " + username);
    return new Authenticator() {
        protected PasswordAuthentication getPasswordAuthentication() {
            System.out.println("Autenticar " + username);
            return new PasswordAuthentication(username, password.toCharArray());
        }
    };
}

EWSClient.useSAAJAPI(true);
System.setProperty("http.auth.preference", "NTLM");
Authenticator.setDefault(getAuthenticator("user", "pw", ""));
IEWSClient client = EWSClient.getEWSClient(new URL("https://domain.com/ews/Exchange.asmx"));
~~~


~~~Java
static Authenticator getAuthenticator() {

    // Este bloco é escrito para suprimir um bug na implementação da sun.
    // Na implementação da Sun o cliente não autentica o usuário para cada conexão,
    // usa credenciais em cache em vez disso.
    sun.net.www.protocol.http.AuthCacheValue.setAuthCache(new sun.net.www.protocol.http.AuthCache() {
        public void remove(String pkey, sun.net.www.protocol.http.AuthCacheValue entry) {
        }
        public void put(String pkey, sun.net.www.protocol.http.AuthCacheValue value) {
        }
        public sun.net.www.protocol.http.AuthCacheValue get(String pkey, String skey) {
            return null;
        }
    });

    return new Authenticator() {
        protected PasswordAuthentication getPasswordAuthentication() {
            return getEmbeddedCredentials(getRequestingURL());
        }

        PasswordAuthentication getEmbeddedCredentials(URL url) {
            if (url == null) {
                return null;
            }
            String userInfo = url.getUserInfo();
            int colon = userInfo == null ? -1 : userInfo.indexOf(":");
            if (colon == -1) {
                return null;
            } else {
                String userName = userInfo.substring(0, colon);
                String pass;
                try {
                    pass = URLDecoder.decode(userInfo.substring(colon + 1), "UTF-8");
                } catch (UnsupportedEncodingException e) {
                    pass = "";
                }
                System.out.println("Autenticar " + userInfo);
                return new PasswordAuthentication("\\" + userName, pass.toCharArray());
            }
        }
    };
}

static URL getURL(String url, String user, String pw, String domain) throws Exception {
    String host = new URL(url).getHost();
    URL endpoint = new URL(url.replace(host, user + ":" + URLEncoder.encode(pw, "UTF-8") + "@" + host));

    return endpoint;
}

EWSClient.useSAAJAPI(true);
Authenticator.setDefault(getAuthenticator());

System.setProperty("http.auth.preference", "NTLM");
IEWSClient client1 = EWSClient.getEWSClient(getURL("https://domain.com/ews/Exchange.asmx", "user1", "pw", "domain"));
IEWSClient client2 = EWSClient.getEWSClient(getURL("https://domain.com/ews/Exchange.asmx", "user2", "pw", "domain"));
~~~


Desde o Java 9, o Autenticador pode ser definido para conexão:

~~~Java
static Map<String, Authenticator> authInfo = new HashMap<String, Authenticator>();
static URL getURL(String url, final String user, final String pw, final String domain) throws MalformedURLException {
    URL endpoint = new URL(new URL(url), "", new URLStreamHandler() {
        protected URLConnection openConnection(URL url) throws IOException {
            URL target = new URL(url.toString());
            HttpURLConnection connection = (HttpURLConnection) target.openConnection();
            // Cache para User@Url
            Authenticator auth = authInfo.get(user + "@" + url);
            if (auth == null) {
                auth = new Authenticator() {
                    protected PasswordAuthentication getPasswordAuthentication() {
                        System.out.println("Autenticar " + user);
                        return new PasswordAuthentication(domain + "\\" + user, pw.toCharArray());
                    }
                };
                authInfo.put(user + "@" + url, auth);
            }
            connection.setAuthenticator(auth);

            return connection;
        }
    });

    return endpoint;
}

EWSClient.useSAAJAPI(true);
System.setProperty("http.auth.preference", "NTLM");
IEWSClient client1 = EWSClient.getEWSClient(getURL("https://domain.com/ews/Exchange.asmx", "user1", "pw", "domain"));
IEWSClient client2 = EWSClient.getEWSClient(getURL("https://domain.com/ews/Exchange.asmx", "user2", "pw", "domain"));
~~~


{{% alert color="primary" %}} 

Nota:
As APIs JAXB são consideradas APIs Java EE e, portanto, não estão mais contidas no caminho de classe padrão em Java SE 9.

{{% /alert %}} 

Dependências JAXB do Maven:

~~~  
<dependency>
    <groupId>javax.xml.bind</groupId>
    <artifactId>jaxb-api</artifactId>
</dependency>
<dependency>
    <groupId>com.sun.xml.bind</groupId>
    <artifactId>jaxb-impl</artifactId>
</dependency>
<dependency>
    <groupId>com.sun.xml.bind</groupId>
    <artifactId>jaxb-core</artifactId>
</dependency>
<dependency>
    <groupId>com.sun.xml.messaging.saaj</groupId>
    <artifactId>saaj-impl</artifactId>
</dependency>
~~~

## **Usar AutodiscoverService**
O seguinte exemplo de código demonstra o uso de [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) para TLS 1.2

~~~Java
AutodiscoverService service = new AutodiscoverService();
service.setCredentials(new NetworkCredential("user", "password"));
GetUserSettingsResponse response = service.getUserSettings("userSmtpAddress", UserSettingName.ExternalEwsUrl, UserSettingName.UserDisplayName);
~~~