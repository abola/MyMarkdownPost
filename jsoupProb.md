## Jsoup 很好，但有問題 ##

Jsoup提供了非常實用的HTML/XML解析工具

## 爬蟲包改良了什麼？ ##

- 整合 Apache Commmons VFS 2.1

    >- 支援更多傳輸協定 (FTP/SFTP/SMB/... )
    >- 支援解壓格式 (gz/zip/tar/... )
    >- 更棒的是，以上你都只要一行程式，就可以完成

- 爬蟲包的SSL是免簽的！

    >  Java 蟲友使用 Jsoup 爬部份 https 網站時(如PTT)，有時會碰到SSL上的問題如下。爬蟲包建立的過程中，會自行產生簽章(Self-signed Server Certificates)，你不需要為了簽章的問題煩腦。
```java
javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:192)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1949)
	at sun.security.ssl.Handshaker.fatalSE(Handshaker.java:302)
	at sun.security.ssl.Handshaker.fatalSE(Handshaker.java:296)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1506)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:216)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:979)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:914)
	... 20 more
Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
	at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:387)
	at sun.security.validator.PKIXValidator.engineValidate(PKIXValidator.java:292)
	at sun.security.validator.Validator.validate(Validator.java:260)
	at sun.security.ssl.X509TrustManagerImpl.validate(X509TrustManagerImpl.java:324)
	at sun.security.ssl.X509TrustManagerImpl.checkTrusted(X509TrustManagerImpl.java:229)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:124)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1488)
	... 20 more
Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
	at sun.security.provider.certpath.SunCertPathBuilder.build(SunCertPathBuilder.java:146)
	at sun.security.provider.certpath.SunCertPathBuilder.engineBuild(SunCertPathBuilder.java:131)
	at java.security.cert.CertPathBuilder.build(CertPathBuilder.java:280)
	at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:382)
	... 26 more
```
