FROM perl:5.22

RUN cpanm -n \
		DBI \
		DBD::mysql \
		Term::ReadKey \
	&& curl -sSL https://percona.com/get/pt-show-grants > /usr/bin/pt-show-grants \
	&& chmod +x /usr/bin/pt-show-grants \
	&& rm -rf /root/.cpanm

ENTRYPOINT ["pt-show-grants"]
