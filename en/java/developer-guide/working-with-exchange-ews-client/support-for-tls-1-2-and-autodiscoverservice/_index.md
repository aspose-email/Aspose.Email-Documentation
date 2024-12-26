---
title: Support for TLS 1.2 and AutodiscoverService
ArticleTitle: Support for TLS 1.2 and AutodiscoverService
type: docs
weight: 180
url: /java/support-for-tls-1-2-and-autodiscoverservice/
---

Aspose.Email for Java now supports TLS 1.2 by using SAAJ API. The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) provides a static property [useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)) which can be set to **true** for using TLS 1.2. Aspose.Email for Java also supports [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) for TLS 1.2. The following code samples demonstrate the use of SAAJ API and [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) for TLS 1.2.
## **Use SAAJ API**
The Java EE SOAP Client used with SAAJAPI mode - <https://docs.oracle.com/cd/E19651-01/817-2151-10/wsgjaxm.html>. 


The following code sample demonstrates using the SAAJ API by setting [EWSClient.useSAAJAPI](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient#useSAAJAPI\(boolean\)) property to **true**.

In the next code snippet Basic authentication header will be assigned:


~~~Java
EWSClient.useSAAJAPI(true);
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testuser", "pw", "domain");
client.listMessages();
~~~
In the next code snippet OAUTH2 authentication header will be assigned:


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

Note that in this mode, the API does not control the NTLM authentication process.
Java Authenticator is required for NTLM authentication.

{{% /alert %}} 


The NTLM authentication code snippet for Java 8:

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

    // This block is written for suppressing a bug in sun implementation.
    // In Sun Impl client doesn't authenticate user for each connection,
    // uses cached credentials instead.
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

Since Java 9, the Authenticator can be set for connection:


~~~Java
static Map<String, Authenticator> authInfo = new HashMap<String, Authenticator>();
static URL getURL(String url, final String user, final String pw, final String domain) throws MalformedURLException {
    URL endpoint = new URL(new URL(url), "", new URLStreamHandler() {
        protected URLConnection openConnection(URL url) throws IOException {
            URL target = new URL(url.toString());
            HttpURLConnection connection = (HttpURLConnection) target.openConnection();
            // Cache for User@Url
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

Note:
The JAXB APIs are considered to be Java EE APIs, and therefore are no longer contained on the default class path in Java SE 9.

{{% /alert %}} 

Maven JAXB dependencies:

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

## **Use AutodiscoverService**
The following code sample demonstrates the use of [AutodiscoverService](https://apireference.aspose.com/email/java/com.aspose.email/AutodiscoverService) for TLS 1.2


~~~Java
AutodiscoverService service = new AutodiscoverService();
service.setCredentials(new NetworkCredential("user", "password"));
GetUserSettingsResponse response = service.getUserSettings("userSmtpAddress", UserSettingName.ExternalEwsUrl, UserSettingName.UserDisplayName);
~~~
