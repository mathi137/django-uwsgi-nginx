FROM python:3.12

# Define an argument to receive values from docker-compose
ARG WORKDIR

# Set environment variables
ENV PYTHONUNBUFFERED 1
ENV WORKDIR=${WORKDIR}

# Set working directory
WORKDIR ${WORKDIR}

# Install dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy the Django project
COPY . .

# Collect static files
RUN python manage.py collectstatic --noinput

# Expose port for uwsgi
EXPOSE 8000

# Run the Django development server
CMD ["uwsgi", "--ini", "${WORKDIR}/uwsgi.ini"]