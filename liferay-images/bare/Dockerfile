FROM amazonlinux
MAINTAINER Hua Luo <hluo997@gmail.com>

## install required tools and Oracle JDK
RUN yum -y install findutils \
	&& yum -y install wget \
	&& yum -y install zip unzip \
	&& yum -y remove java* \
	&& wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u111-b14/jdk-8u111-linux-x64.rpm \	
	&& rpm -Uvh jdk-8u111-linux-x64.rpm \
	&& rm jdk-8u111-linux-x64.rpm

## install imagemagick
RUN yum -y install ImageMagick

COPY openoffice/ /openoffice/

## set up open office server and add service script.
RUN wget http://download.documentfoundation.org/libreoffice/stable/5.2.3/rpm/x86_64/LibreOffice_5.2.3_Linux_x86-64_rpm.tar.gz \
	&& tar -xvf LibreOffice_5.2.3_Linux_x86-64_rpm.tar.gz -C / \
	&& yum -y install LibreOffice_5.2.3.3_Linux_x86-64_rpm/RPMS/*.rpm \
	&& rm LibreOffice_5.2.3_Linux_x86-64_rpm.tar.gz \
	&& rm -Rf LibreOffice_5.2.3.3_Linux_x86-64_rpm \
	&& yum -y install dbus-glib \
	&& yum -y install cairo \
	&& yum -y install cups \
	&& cp /openoffice/etc_init_d_openoffice /etc/init.d/openoffice \
	&& chmod 755 /etc/init.d/openoffice \
	&& sed -i -e 's/\r//g' /etc/init.d/openoffice \
	&& chkconfig --add openoffice \
	&& rm -Rf /openoffice
	
COPY liferay/ /liferay/

## set up liferay installation and add service script
RUN curl -fSL https://sourceforge.net/projects/lportal/files/Liferay%20Portal/7.0.2%20GA3/liferay-ce-portal-tomcat-7.0-ga3-20160804222206210.zip/download -o liferay-ce-portal-tomcat-7.0-ga3-20160804222206210.zip \
	&& unzip liferay-ce-portal-tomcat-7.0-ga3-20160804222206210.zip -d /opt \
	&& rm liferay-ce-portal-tomcat-7.0-ga3-20160804222206210.zip \
	&& cp /liferay/aws-dynamodb-session-tomcat-2.0.4.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/lib \	
	&& cp /liferay/webapps-lib/poi-3.13.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib/poi.jar \
	&& cp /liferay/webapps-lib/poi-ooxml-3.13.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib/poi-ooxml.jar \
	&& cp /liferay/webapps-lib/poi-ooxml-schemas-3.13.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib/poi-ooxml-schemas.jar \
	&& cp /liferay/webapps-lib/poi-scratchpad-3.13.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib/poi-scratchpad.jar \
	&& cp /liferay/webapps-lib/xuggle-xuggler-arch-x86_64-pc-linux-gnu.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib \
	&& cp /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/webapps/ROOT/WEB-INF/lib/xercesImpl.jar /opt/liferay-ce-portal-7.0-ga3/tomcat-8.0.32/lib/ext \
	&& mkdir /opt/liferay-ce-portal-7.0-ga3/osgi/modules \
	&& cp /liferay/etc_init_d_liferay /etc/init.d/liferay \
	&& chmod 755 /etc/init.d/liferay \
	&& sed -i -e 's/\r//g' /etc/init.d/liferay \
	&& chkconfig --add liferay \	
	&& rm -Rf /liferay
