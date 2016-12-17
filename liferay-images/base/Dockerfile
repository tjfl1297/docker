FROM hluo997/liferay:bare
MAINTAINER Hua Luo <hluo997@gmail.com>

COPY custom/ /custom/
	
## add custom configurations, modules and entrypoint script.
RUN cp /custom/osgi/configs/* /opt/liferay-ce-portal-7.0-ga3/osgi/configs \
	&& cp /custom/osgi/marketplace/override/* /opt/liferay-ce-portal-7.0-ga3/osgi/marketplace/override \
	&& cp /custom/osgi/modules/* /opt/liferay-ce-portal-7.0-ga3/osgi/modules \
	&& cp /custom/docker-entrypoint.sh / \	
	&& sed -i -e 's/\r//g' /docker-entrypoint.sh \	
	&& rm -Rf /custom
