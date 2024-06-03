A simple flask app to remove the background of an image with [Rembg](https://github.com/danielgatis/rembg)

Based on https://github.com/codediodeio/rembg-webapp-tutorial with some modifications


## Running application locally

1. Clone: https://github.com/Zabir-A/Background-Remover-V2/
2. Clone: https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx into project directory

```
pip install -r requirements.txt
python app.py
```

## Running the application in Docker 

1. Build the image:
```
docker build -t <your-image-name>:<tag> .
```

2. Running the Docker container:
```
docker run -d -p <host-port>:<container-port> --name <your-container-name> <your-image-name>:<tag>
```

### Running on ARM Architecture:
#### If you want to run the application on ARM architecture, such as a Raspberry Pi, change the Dockerfile content as shown below:
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
## 1. Build the image for ARM architecture
```
docker run -d -p <host-port>:<container-port> --name <your-arm-container-name> <your-arm-image-name>
```
## 2. Run the Docker container
```
docker run -d -p <host-port>:<container-port> --name <your-arm-container-name> <your-arm-image-name>
```
