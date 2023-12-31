FROM node

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

# Create the app directory
WORKDIR /app

# Copy package.json and package-lock.json separately to leverage Docker cache
COPY package.json .
COPY package-lock.json .

# Install app dependencies with a non-root user
RUN npm install --unsafe-perm=true --allow-root

# Copy the rest of the application files
COPY . .

# Expose the port the app runs on
EXPOSE 16108

# Start the application
CMD ["npm", "start"]
