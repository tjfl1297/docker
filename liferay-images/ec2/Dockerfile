FROM hluo997/liferay:base
MAINTAINER Hua Luo <hluo997@gmail.com>

COPY custom/ /custom/
	
## add custom configurations and properties for production environment
RUN cp /custom/osgi/configs/* /opt/liferay-ce-portal-7.0-ga3/osgi/configs \
	&& cp /custom/portal-ext.properties /opt/liferay-ce-portal-7.0-ga3 \
	&& cp /custom/context.xml /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/conf \
	&& cp /custom/setenv.sh /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/bin \
	&& rm -Rf /custom

EXPOSE 8080/tcp
EXPOSE 11311/tcp

ENTRYPOINT ["/docker-entrypoint.sh"]
