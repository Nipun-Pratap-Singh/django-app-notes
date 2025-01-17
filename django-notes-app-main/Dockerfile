# Use Python 3.9 base image
FROM python:3.9

# Set working directory
WORKDIR /app/backend

# Copy requirements file to the working directory
COPY requirements.txt /app/backend/

# Update system packages and install dependencies
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y gcc default-libmysqlclient-dev pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
RUN pip install --no-cache-dir mysqlclient \
    && pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code to the container
COPY . /app/backend/

# Expose port 8000
EXPOSE 8000

# Run migrations and start the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
