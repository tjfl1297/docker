FROM hluo997/liferay:bare
MAINTAINER Hua Luo <hluo997@gmail.com>

COPY custom/ /custom/
	
## add custom configurations, modules and properties.
RUN cp /custom/osgi/configs/*.cfg /opt/liferay-ce-portal-7.0-ga3/osgi/configs \
	&& cp /custom/osgi/marketplace/override/*.jar /opt/liferay-ce-portal-7.0-ga3/osgi/marketplace/override \	
	&& cp /custom/osgi/modules/*.jar /opt/liferay-ce-portal-7.0-ga3/osgi/modules \
	&& cp /custom/portal-ext.properties /opt/liferay-ce-portal-7.0-ga3 \	
	&& rm -Rf /custom
