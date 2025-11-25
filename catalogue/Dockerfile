FROM node:20.19.5-alpine3.21 AS build 
WORKDIR /opt/server  
COPY package.json . 
COPY *.js . 
# this may add extra cache memory
RUN npm install 


FROM node:20.19.5-alpine3.21
WORKDIR /opt/server 
# Create a group and user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop  
RUN chown -R roboshop:roboshop /opt/server
EXPOSE 8080  
LABEL com.project="roboshop" \
      component="catalogue" \
      created_by="siva"
ENV MONGO="true" \ 
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]
COPY --from=build --chown=roboshop:roboshop /opt/server/ /opt/server/
USER roboshop 

# FROM node:20 
# WORKDIR /opt/server 
# EXPOSE 8080 
# COPY package.json . 
# COPY *.js . 
# RUN npm install 
# ENV MONGO="true" \ 
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]

