FROM nginx:stable-alpine

COPY ./docker/nginx/templates /etc/nginx/templates

# Copy the content of Laravel's public directory
COPY ./working_laravel/public /var/www/html/public

WORKDIR /var/www/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]