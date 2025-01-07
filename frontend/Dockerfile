FROM node:14-alpine

WORKDIR /app

# install application dependencies
COPY . .
RUN npm install
# RUN npm install react-scripts -g

# copy app files
EXPOSE 3000
CMD ["npm", "start"]
