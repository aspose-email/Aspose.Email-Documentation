---
title: "Поддержка TLS 1.2 и AutodiscoverService"
url: /ru/java/support-for-tls-1-2-and-autodiscoverservice/
weight: 180
type: docs
---

Aspose.Email для Java теперь поддерживает TLS 1.2 с использованием SAAJ API. [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) предоставляет статическое свойство [useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)), которое можно установить в **true** для использования TLS 1.2. Aspose.Email для Java также поддерживает [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) для TLS 1.2. Следующие примеры кода демонстрируют использование SAAJ API и [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) для TLS 1.2.
## **Использование SAAJ API**
Java EE SOAP клиент, используемый в режиме SAAJAPI - <https://docs.oracle.com/cd/E19651-01/817-2151-10/wsgjaxm.html>. 

Следующий пример кода демонстрирует использование SAAJ API, устанавливая свойство [EWSClient.useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)) в **true**.

В следующем фрагменте кода будет присвоен заголовок базовой аутентификации:

~~~Java
EWSClient.useSAAJAPI(true);
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testuser", "pw", "domain");
client.listMessages();
~~~
В следующем фрагменте кода будет присвоен заголовок аутентификации OAUTH2:

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

Обратите внимание, что в этом режиме API не контролирует процесс аутентификации NTLM.
Java Authenticator требуется для аутентификации NTLM.

{{% /alert %}} 

Код аутентификации NTLM для Java 8:

~~~Java
import java.net.Authenticator;
import java.net.PasswordAuthentication;
import java.net.URL;

static Authenticator getAuthenticator(String user, String pw, String domain) {
    final String username = domain + "\\" + user;
    final String password = pw;
    System.out.println("New Credentials " + username);
    return new Authenticator() {
        protected PasswordAuthentication getPasswordAuthentication() {
            System.out.println("Authenticate " + username);
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

    // Этот блок написан для устранения ошибки в реализации sun.
    // В реализации Sun клиент не аутентифицирует пользователя для каждого соединения,
    // вместо этого использует кэшированные учетные данные.
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
                System.out.println("Authenticate " + userInfo);
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


С версии Java 9 Authenticator можно настроить для подключения:

~~~Java
static Map<String, Authenticator> authInfo = new HashMap<String, Authenticator>();
static URL getURL(String url, final String user, final String pw, final String domain) throws MalformedURLException {
    URL endpoint = new URL(new URL(url), "", new URLStreamHandler() {
        protected URLConnection openConnection(URL url) throws IOException {
            URL target = new URL(url.toString());
            HttpURLConnection connection = (HttpURLConnection) target.openConnection();
            // Кэш для User@Url
            Authenticator auth = authInfo.get(user + "@" + url);
            if (auth == null) {
                auth = new Authenticator() {
                    protected PasswordAuthentication getPasswordAuthentication() {
                        System.out.println("Authenticate " + user);
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

Примечание:
JAXB API считаются API Java EE и, следовательно, больше не включены в путь классов по умолчанию в Java SE 9.

{{% /alert %}} 

Зависимости Maven для JAXB:

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

## **Использование AutodiscoverService**
Следующий пример кода демонстрирует использование [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) для TLS 1.2

~~~Java
AutodiscoverService service = new AutodiscoverService();
service.setCredentials(new NetworkCredential("user", "password"));
GetUserSettingsResponse response = service.getUserSettings("userSmtpAddress", UserSettingName.ExternalEwsUrl, UserSettingName.UserDisplayName);
~~~