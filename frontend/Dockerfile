FROM nginx:alpine

# Copy the frontend files from the current directory to the Nginx web root
COPY . /usr/share/nginx/html

# Expose port 80 for HTTP access
EXPOSE 80 

# Start nginx
CMD ["nginx", "-g", "daemon off;"]