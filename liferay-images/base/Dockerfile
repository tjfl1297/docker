FROM hluo997/liferay:bare
MAINTAINER Hua Luo <hluo997@gmail.com>

COPY custom/ /custom/
	
## add custom configurations, modules, precompiled jsps and entrypoint script.
RUN cp /custom/osgi/configs/* /opt/liferay-ce-portal-7.0-ga3/osgi/configs \
	&& cp /custom/osgi/marketplace/override/* /opt/liferay-ce-portal-7.0-ga3/osgi/marketplace/override \
	&& cp /custom/osgi/modules/* /opt/liferay-ce-portal-7.0-ga3/osgi/modules \	
	&& unzip /custom/precompiled/osgi.zip -d /opt/liferay-ce-portal-7.0-ga3/work \	
	&& unzip /custom/precompiled/ROOT.zip -d /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/work/Catalina/localhost \		
	&& cp /custom/docker-entrypoint.sh / \
	&& chmod 755 /docker-entrypoint.sh \
	&& sed -i -e 's/\r//g' /docker-entrypoint.sh \	
	&& rm -Rf /custom
