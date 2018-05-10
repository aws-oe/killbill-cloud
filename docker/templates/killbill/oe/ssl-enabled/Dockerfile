FROM killbill/killbill:0.18.19

COPY --chown=tomcat7:tomcat7 ./plugins/killbill-braintree_blue-0.3.1/  $KILLBILL_HOME/bundles/plugins/ruby/

USER root

RUN chown tomcat7:tomcat7 /var/lib/killbill/bundles/plugins

RUN apt-get update && apt-get install -y \
        ssl-cert \
        && apt-get clean

RUN usermod -a -G ssl-cert tomcat7

COPY server.xml /var/lib/tomcat7/conf/server.xml

USER tomcat7
WORKDIR $TOMCAT_HOME

EXPOSE 8443
