# Pull a base image from a trusted source
FROM ubuntu:20.04

# Update and install necessary packages
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Create a new user
RUN useradd -ms /bin/bash appuser

# Establishs the working directory
WORKDIR /app

# Copy the application files
COPY . /app

# Install Python3 dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Change ownership of the application files to the new user
RUN chown -R appuser:appuser /app

# Switch to the new user
USER appuser

# Command to run the application
CMD ["python3", "app.py"]
