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


# Set working directory
WORKDIR /opt/server

# Copy Python files
COPY *.py .

# Copy uWSGI config
COPY payment.ini .

# Install dependencies
COPY requirements.txt .
RUN pip3 install -r requirements.txt

# Set environment variables
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
