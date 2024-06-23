FROM python:3.10-slim

WORKDIR /code

# Install dependencies
COPY requirements.txt /code/

RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc libc-dev \
    && pip install --upgrade pip \
    && pip install -r requirements.txt \
    && apt-get purge -y --auto-remove gcc libc-dev \
    && rm -rf /var/lib/apt/lists/*

# Copy the application code
COPY . /code/

# Expose port 8000
EXPOSE 8000

# Run the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
