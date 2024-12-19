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
RUN \
	apt-get update && apt-get install -y \
	nano\
	proftpd

# Se copian la plantilla web 
COPY ./Recursos_C1 /srv/ftp/Recursos_C1

# Se copian los archivos de configuaración
COPY ./conf/proftpd.conf /etc/proftpd/proftpd.conf

# Puertos
EXPOSE 21 50000-50030

