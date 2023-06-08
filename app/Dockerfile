# Start from the official Base Image
FROM python:3.10

# Update
RUN apt-get update && apt-get upgrade -y

# Copy the file with the requirements to the '/app' directory.
COPY requirements.txt .

# Install requirements
RUN pip install --no-cache-dir --upgrade -r ./requirements.txt

# Copy all of the code from the origin to the docker mounted directory
ADD . .
WORKDIR .
