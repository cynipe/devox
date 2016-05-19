FROM python:2.7

RUN apt-get update && apt-get install -y --no-install-recommends git \
	&& git clone --depth 1 https://github.com/jupyter/jupyter-drive /tmp/jupyter-drive \
	&& pip install --no-cache-dir  \
		jupyter \
		terminado \
		pyzmq \
		/tmp/jupyter-drive \
	&& rm -rf \
		/var/lib/apt/lists/** \
		/tmp/**

ENV JUPYTER_PORT=8888
COPY boot-jupyter /boot-jupyter
CMD ["/boot-jupyter"]
