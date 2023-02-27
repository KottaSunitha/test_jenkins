FROM ovaledgellc/ovaledge:tomcat-9.0.58

MAINTAINER info@ovaledge.com

ENV DEFAULT_OVALEDGE_BIGQUERY_MAX_CONNECTIONS=10

#RUN apk update && apk add curl && apk add jq
#RUN apk add --no-cache \
 #       python3 \
  #      py3-pip \
   # && pip3 install --upgrade pip \
   # && pip3 install --no-cache-dir \
    #    awscli \
    #&& rm -rf /var/cache/apk/*

#RUN aws --version 
RUN mkdir -p /home/ovaledge/third_party_jars
#RUN apk add --no-cache openssl
RUN mkdir -p /home/ovaledgefiles
RUN mkdir -p /home/data
RUN mkdir -p /usr/local/tomcat/conf/saml
RUN mkdir -p /home/ovaledge/Certificates
RUN chmod 777 -R /usr/local/tomcat/

COPY rds-ca-2019-root.pem /home/ovaledge/Certificates/rds-ca-2019-root.pem
COPY rds-combined-ca-bundle.pem /home/ovaledge/Certificates/rds-combined-ca-bundle.pem
COPY greenplum-jdbc-5.1.4.jar /home/ovaledge/third_party_jars/greenplum-jdbc-5.1.4.jar
COPY postgresql-42.1.1.jar /home/ovaledge/third_party_jars/postgresql-42.1.1.jar
COPY snowflake-jdbc-3.12.12.jar /home/ovaledge/third_party_jars/snowflake-jdbc-3.12.12.jar
COPY vertica-jdbc-7.0.1-0.jar /home/ovaledge/third_party_jars/vertica-jdbc-7.0.1-0.jar
COPY ojdbc6.jar /home/ovaledge/third_party_jars/ojdbc6.jar
COPY sqljdbc41.jar /home/ovaledge/third_party_jars/sqljdbc41.jar
COPY terajdbc4.jar /home/ovaledge/third_party_jars/terajdbc4.jar
COPY RedshiftJDBC42-no-awssdk-1.2.37.1061.jar /home/ovaledge/third_party_jars/RedshiftJDBC42-no-awssdk-1.2.37.1061.jar
COPY qds-jdbc-2.3.2.jar /home/ovaledge/third_party_jars/qds-jdbc-2.3.2.jar
COPY db2jcc4-10.1.jar /home/ovaledge/third_party_jars/db2jcc4-10.1.jar
COPY mongojavadriver3.4.3.jar /home/ovaledge/third_party_jars/mongojavadriver3.4.3.jar
COPY ngdbc-2.2.16.jar /home/ovaledge/third_party_jars/ngdbc-2.2.16.jar

#RUN mkdir -p /usr/local/tomcat/conf/glowroot/
#RUN mkdir -p /usr/local/tomcat/conf/glowroot/lib/
#RUN mkdir -p /home/ovaledge/Certificates/
#COPY glowroot/glowroot.jar /usr/local/tomcat/conf/glowroot/glowroot.jar
#COPY glowroot/admin.json /usr/local/tomcat/conf/glowroot/admin.json
#COPY glowroot/lib/glowroot-central-collector-https-linux-alpine.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-central-collector-https-linux-alpine.jar
#COPY glowroot/lib/glowroot-central-collector-https-linux.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-central-collector-https-linux.jar
#COPY glowroot/lib/glowroot-central-collector-https-osx.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-central-collector-https-osx.jar
#COPY glowroot/lib/glowroot-central-collector-https-windows.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-central-collector-https-windows.jar
#COPY glowroot/lib/glowroot-embedded-collector.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-embedded-collector.jar
#COPY glowroot/lib/glowroot-logging-logstash.jar /usr/local/tomcat/conf/glowroot/lib/glowroot-logging-logstash.jar
#RUN chmod 777 -R /usr/local/tomcat/conf/glowroot/
RUN wget https://jenkins-ovaledge-s3.s3.amazonaws.com/Release6.0.0.X_HDFS/119/ovaledge.war -P /root/temp/
#COPY ovaledge.war /root/temp/ovaledge.war
COPY catalina.properties /root/temp/catalina.properties
COPY ap-south-1-bundle.pem  /home/ovaledge/Certificates/ap-south-1-bundle.pem
COPY rds-combined-ca-bundle.pem /home/ovaledge/Certificates/rds-combined-ca-bundle.pem
#COPY gateway.cer /home/ovaledge/Certificates/gateway.cer
#COPY qa-gateway.cer /home/ovaledge/Certificates/qa-gateway.cer
#COPY dev.cer  /home/ovaledge/Certificates/dev.cer
COPY prod-ax-gateway.cer /home/ovaledge/Certificates/prod-ax-gateway.cer
#COPY tableau.cer  /home/ovaledge/Certificates/tableau.cer
#COPY prod.cer  /home/ovaledge/Certificates/prod.cer
COPY keystore.jks /usr/local/tomcat/conf/saml/keystore.jks
#COPY glowroot.jar /usr/local/tomcat/bin/setenv.sh

#EXPOSE 4000
EXPOSE 8080

COPY run.sh /run.sh

ENTRYPOINT ["/run.sh"]
