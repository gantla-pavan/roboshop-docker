# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server/payment.ini
# COPY *.py .
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt
# ENV CART_HOST="cart" \
#      CART_PORT="8080" \
#      USER_HOST="user" \
#      USER_PORT="8080" \
#      AMPQPHOST="rabbitmq" \
#      AMQP_USER="roboshop" \
#     AMQP_PASSWORD="roboshop123"

# CMD ["uwsgi", "--ini", "payment.ini"]


# Use Python 3.9
FROM python:3.9

# Set working directory
WORKDIR /opt/server

# Copy Python source files
COPY *.py .

# Copy uWSGI config
COPY payment.ini .

# Copy requirements and install
COPY requirements.txt .
RUN pip3 install -r requirements.txt

# Environment variables
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMPQPHOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASSWORD="roboshop123"

# Expose port
EXPOSE 8080

# Run uWSGI
CMD ["uwsgi", "--ini", "payment.ini"]
