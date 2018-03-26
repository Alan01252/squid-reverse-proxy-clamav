FROM ubuntu:latest
RUN apt-get update
RUN apt -y -f install clamav clamav-daemon c-icap && freshclam
RUN apt -y -f install wget build-essential libicapapi-dev
COPY c-icap.conf /etc/c-icap/c-icap.conf
COPY squidclamav.conf /etc/squidclamav.conf
RUN cd /usr/src/ && wget https://vorboss.dl.sourceforge.net/project/squidclamav/squidclamav/6.16/squidclamav-6.16.tar.gz -o squidclam.tar.gz && \
		tar xzf squidclamav-6.16.tar.gz && \
	cd squidclamav-6.16 && \
	./configure --with-c-icap=/etc/c-icap/ && make -j 2 && make install
RUN sed -i "s|START=no|START=yes|g" /etc/default/c-icap
RUN mkdir -p /var/run/c-icap/ && chmod 777 /var/run/c-icap
