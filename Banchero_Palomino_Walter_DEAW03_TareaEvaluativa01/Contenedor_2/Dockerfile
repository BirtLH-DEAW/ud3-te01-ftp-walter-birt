# Crea una nueva imagen a partir de ubuntu

FROM ubuntu:latest

# Da información sobre la imagen que estamos creando
# Podemos usar la \ para encadenar todos los valores
LABEL \
	authors="DEAW" \
	version="2.0" \
	description="DEAW03. Tarea evaluativa 1" 

# Ejecutamos diferentes comandos
# Debemos encadenarlos en un mismo RUN mediante la \
RUN apt-get update && apt-get install -y \
    nano \
    proftpd \
    openssl \
    proftpd-mod-crypto


# Crear el usuario deaw, contraseña deaw y la carpeta deaw 
RUN useradd -m -d /srv/deaw -s /usr/sbin/nologin deaw && \
    echo "deaw:deaw" | chpasswd && \ 
    mkdir -p /srv/deaw && \ 
    chown -R deaw:deaw /srv/deaw


# Se copian las plantillas web 
COPY ./Recursos_C2/* /srv/deaw/

# Se copian los archivos de configuaración
COPY ./conf/proftpd.conf /etc/proftpd/
COPY ./conf/tls.conf /etc/proftpd/
COPY ./conf/modules.conf /etc/proftpd/

# Se copian los certificados
COPY ./conf/certs/proftpd_crt.pem /etc/ssl/certs/proftpd_crt.pem
COPY ./conf/certs/proftpd_key.pem /etc/ssl/private/proftpd_key.pem

# Puertos
EXPOSE 21 50000-50030

