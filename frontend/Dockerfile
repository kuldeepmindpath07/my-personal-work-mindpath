FROM node:14-alpine

WORKDIR /app

# install application dependencies
COPY package*.json ./
RUN npm install
# RUN npm install react-scripts -g

# copy app files
COPY . .

EXPOSE 3000
CMD ["npm", "start"]
