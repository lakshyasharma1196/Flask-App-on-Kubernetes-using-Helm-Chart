# Use an official Python runtime as a parent image
FROM python:2.7-slim-buster

ENV SQLALCHEMY_DATABASE_URI=$SQLALCHEMY_DATABASE_URI
COPY ./dashboard/requirements.txt /requirements.txt
RUN chmod +x /requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

RUN mkdir -p /app
COPY . /app
WORKDIR /app/dashboard

ENV PYTHONPATH=/app/dashboard

# Expose port 5000
EXPOSE 5000

# Define environment variables
ENV FLASK_APP=main.py
ENV FLASK_ENV=production
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# Run the command to start the Flask application
CMD ["flask", "run", "--host=0.0.0.0"]

