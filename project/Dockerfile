# Use an official Python runtime as a parent image
FROM yoanlin/opencv-python3-tensorflow:latest

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 2500 available to the world outside this container
EXPOSE 2500

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
