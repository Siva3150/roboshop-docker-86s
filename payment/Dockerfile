# FROM python:3 As build
# WORKDIR /opt/server  
# COPY payment.ini .
# COPY *.py .
# COPY requirements.txt . 
# RUN pip3 install -r requirements.txt  

# FROM python:3
# WORKDIR /opt/server
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
#     chown -R roboshop:roboshop /opt/server  
# EXPOSE 8080  
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server 
# CMD ["uwsgi", "--ini", "payment.ini"] 


FROM python:3 
WORKDIR /opt/server 
EXPOSE 8080 
COPY payment.ini .
COPY *.py .
COPY requirements.txt . 
RUN pip3 install -r requirements.txt 
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123" 
CMD ["uwsgi", "--ini", "payment.ini"] 


