

####  Install certificate for your website 

- Buy certificate for your domain 

  There are many website offer certification , follow instruction you will be able to get the related certificate files for your domain



- Assume you got related certification files for your doamin  (I got them from https://www.ssls.com/)

  mainriversoft_com.crt   -> server certificate

  mainriversoft_com_key.txt  -> private key 

  mainriversoft_com.ca-bundle  -> Root & Intermediate Certificate Bundle

  E.g,  if you have them seperately as serveal files you could make them as one bundle file, for details click the link https://support.comodo.com/index.php?/Knowledgebase/Article/View/1145/1/how-do-i-make-my-own-bundle-file-from-crt-files


- You generate/export the keystore file by below command, you need to create keystorepass which will be used by server.xml configuration later on

  `openssl pkcs12 -export -in mainriversoft_com.crt -inkey mainriversoft_com_key.txt -certfile mainriversoft_com.ca-bundle -name mrscert -out mainriversoft_com.p12`

  alias name of server certificate is mrscert

  keystore file is mainriversoft_com.p12

- install keystore into tomcat 

  - stop tomcat on ubuntu linux 
  
    `systemctl stop tomcat`

  - modify tomcat/config/server.xml to setup keystore for tomcat 
  
     ![ssl1](./images/ssl1.png)
 
  - modify tomcat/config/web.xml for redirect http to https         
  
     ![ssl2](./images/ssl2.png)
   
  - start tomcat on ubuntu linux
  
     `systemctl start tomcat`

- As you can see, it works!

    ![ssl2](./images/ssl3.png)


