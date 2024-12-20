# Nginx Dockerfile
FROM nginx:1.27.3

# Install gettext for envsubst
RUN apt-get update && apt-get install -y gettext-base && rm -rf /var/lib/apt/lists/*

# Copy the Nginx configuration template
COPY nginx.conf /etc/nginx/nginx.conf.template

# Use envsubst to replace variables and start Nginx
CMD envsubst '${WORKDIR} ${SERVER_NAME} ${SERVER_PORT}' < /etc/nginx/nginx.conf.template > /etc/nginx/conf.d/default.conf && \
    nginx -g "daemon off;"

# Expose port 80
EXPOSE 80