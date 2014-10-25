# Use latest jboss/base-jdk:7 image as the base

FROM qburstdevops/base 

RUN apt-get update
RUN apt-get install -y wget curl vim supervisor

RUN mkdir -p /var/log/supervisor /opt/jboss

# Set the WILDFLY_VERSION env variable
ENV WILDFLY_VERSION 8.1.0.Final

# Set the JAVA_HOME env variable
ENV JAVA_HOME /opt/jdk1.7.0_67

# Set the JBOSS_HOME env variable
ENV JBOSS_HOME /opt/jboss/wildfly

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content
# Make sure the distribution is available from a well-known place
RUN cd $HOME && curl http://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz | tar zx && mv $HOME/wildfly-$WILDFLY_VERSION /opt/jboss/wildfly

# Expose the ports we're interested in
EXPOSE 8080 8009 9990 9001

# Define administrative credentials
RUN /opt/jboss/wildfly/bin/add-user.sh admin 123qwe --silent

RUN cd /opt/; wget http://jdbc.postgresql.org/download/postgresql-9.1-903.jdbc4.jar

RUN ln -sf /opt/jboss/wildfly/bin/* /usr/bin/

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Set the default command to run on boot
# This will boot WildFly in the standalone-ha mode and bind to all interface
CMD ["/usr/bin/supervisord"]
