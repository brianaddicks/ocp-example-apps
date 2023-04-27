FROM ubi9/php-80

# Add application sources to a directory that the assemble script expects them
# and set permissions so that the container runs without root access
USER 0
ADD src /tmp/src
RUN chown -R 1001:0 /tmp/src
USER 1001

# disable php clear_env
RUN sed -i 's/;clear_env/clear_env/g' /etc/php-fpm.d/www.conf

# Install the dependencies
RUN /usr/libexec/s2i/assemble

# Set the default command for the resulting image
CMD /usr/libexec/s2i/run