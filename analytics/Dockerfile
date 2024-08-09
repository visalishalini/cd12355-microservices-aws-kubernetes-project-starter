# Use an official Python runtime as a parent image
FROM 387581210505.dkr.ecr.us-east-1.amazonaws.com/python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install dependencies
RUN apt-get update && \
    apt-get install -y build-essential libpq-dev && \
    pip install --upgrade pip setuptools wheel && \
    pip install -r analytics/requirements.txt

# Environment variables
ENV DB_USERNAME=myuser \
    DB_HOST=postgresql-service \
    DB_PORT="5432" \
    DB_NAME=mydatabase

# Make port 5153 available to the world outside this container
EXPOSE 5153

# Run app.py when the container launches
CMD ["python", "analytics/app.py"]
