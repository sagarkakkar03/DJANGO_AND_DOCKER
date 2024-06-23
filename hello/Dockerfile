# Pull base image
FROM python:3.10

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Install dependencies
COPY Pipfile Pipfile.lock /code/
RUN pip install --upgrade pip
RUN pip install pipenv
RUN pipenv install --deploy --system

# Copy project
COPY . /code/

# Debug: Check if Django is installed
RUN pip show django

# Expose port 8000
EXPOSE 8000

# Run the application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
