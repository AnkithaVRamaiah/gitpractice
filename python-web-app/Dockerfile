# Use an official Ubuntu base image
FROM ubuntu

# Set the working directory inside the container
WORKDIR /app

# Install Python 3, pip, and venv for creating a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Create a virtual environment inside the container
RUN python3 -m venv /env

# Set the virtual environment's Python and pip to the PATH
ENV PATH="/env/bin:$PATH"

# Copy the requirements file and other necessary files into the container
COPY requirements.txt /app
COPY devops /app

# Install the Python dependencies inside the virtual environment
RUN pip install --upgrade pip && \
    pip install -r requirements.txt

# Set the default command to run the application
ENTRYPOINT ["python3"]
CMD ["devops/manage.py", "runserver", "0.0.0.0:8000"]
