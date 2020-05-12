#Build Phase
FROM node:alpine

WORKDIR '/app'

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

#2nd from statement is new Phase 

FROM nginx

#expose port (for elasticbeanstalk)
EXPOSE 3000

# copy default.conf file

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

#copy from builder phase
COPY --from=0 /app/build /usr/share/nginx/html

#nginx starts automatically