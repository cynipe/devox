FROM php:5.4

# composer
RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer
# need repl huh?
RUN curl -Lo /usr/local/bin/psysh http://psysh.org/psysh \
  && chmod +x /usr/local/bin/psysh

ENTRYPOINT ["/bin/bash"]
