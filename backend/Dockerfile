# Use official Python base image
FROM python:slim

# Set work directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install -r requirements.txt

# Copy app code
COPY app.py .

# Run the app
CMD ["python", "app.py"]
