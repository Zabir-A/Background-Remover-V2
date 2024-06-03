This is a simple Flask web application that utilizes [Rembg](https://github.com/danielgatis/rembg) to remove the background of an image.

It is based on the project found at [codediodeio/rembg-webapp-tutorial](https://github.com/codediodeio/rembg-webapp-tutorial ) with some modifications and minor changes.

## Application Demo

Simply drag and drop an image or browse from files, wait for the application to process and it will download. 

## Running the application locally

1. Clone: https://github.com/Zabir-A/Background-Remover-V2/
2. Clone: https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx into project directory

```
pip install -r requirements.txt
python app.py
```

## Running the application in a Docker container 

1. Build the image:
```
docker build -t <your-image-name>:<tag> .
```

2. Run the Docker container:
```
docker run -d -p <host-port>:<container-port> --name <your-container-name> <your-image-name>:<tag>
```

## Running on ARM Architecture:
### If you want to run the application on ARM architecture, such as a Raspberry Pi, change the Dockerfile content as shown below:
```
FROM python:3.8-slim

COPY u2net.onnx /home/.u2net/u2net.onnx

WORKDIR /app

COPY requirements.txt .

RUN apt-get update && apt-get install -y libpq-dev build-essential

RUN apt-get install cmake -y

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5100

CMD ["python", "app.py"]
```
1. Build the image for ARM architecture
```
docker build --tag <your-image-name>:<tag> --platform linux/arm64 .
```
2. Run the Docker container
```
docker run -d -p <host-port>:<container-port> --name <your-arm-container-name> <your-arm-image-name>
```
