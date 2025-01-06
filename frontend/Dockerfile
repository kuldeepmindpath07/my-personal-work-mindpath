FROM node:16 as build
#using node 16 version base image
WORKDIR /app
#working directory changed as app
COPY . /app
#now install all the dependecies 
RUN npm install
#pulling node image 
FROM node:16
#creating and changing work directory to src
WORKDIR /src
#copying all the files that are present in app folder of build image
COPY --from=build /app /src
#npm start command to run the backend server
CMD ["npm","start"]
