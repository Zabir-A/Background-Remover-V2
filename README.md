This is a web application that removes the background of an image using "AI sorcery".

It utilizes the tool [Rembg](https://github.com/danielgatis/rembg) and project done by codediodeio with some minor changes and bug fixes.

## Application Demo
Simply drag and drop an image, or browse from files. Wait for the application to process and it will download automatically. 

### Original Image 🐕

![Alt text](demo_1.gif)



### Downloaded Image 🐶

![Alt text](demo_2.gif)

## Running the application locally

1. Download & copy the u2net.onnx model into the project's root directory
```
wget https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx
```
2. Install Python dependencies 🐍
```
pip install -r requirements.txt
```
3. Run Python script 🐍
```
python app.py
```

## Running the application in a Docker Container 🐋

1. Build the image:
```
docker build -t <your-image-name>:<tag> .
```

2. Run the Docker container:
```
docker run -d -p <host-port>:<container-port> --name <your-container-name> <your-image-name>:<tag>
```

## Running on ARM Platforms 🍓🥧
#### If you want to run the containerized application on a Raspberry Pi 4/5.

#### Change the default Dockerfile content as shown below:
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
1. Build the image for ARM Platform (linux/arm64)
```
docker build --tag <your-image-name>:<tag> --platform linux/arm64 .
```
2. Run the Docker container
```
docker run -d -p <host-port>:<container-port> --name <your-arm-container-name> <your-arm-image-name>
```
# Windows Installation & Usage

## (Not Recommended)

For those that don't want to go through the trouble, and just want to test it (for fun), there is an packaged executable for the application.

Obviously, this is not how any Web Application (in development) should be used, but, "it just works". 

Please use it at your own risk. 

## Downloading the packaged application (BgRmvr.exe):

1. Download the executable from: https://github.com/Zabir-A/Background-Remover-V2/releases/download/v0.2.0-alpha/BgRmvr.exe

![Alt text](download_exe_page.jpg)

2. Run BgRmvr.exe. It will open up the terminal or CMD (CLI). Wait a few seconds, a window prompt may pop up. Click allow.

![Alt text](allow_prompt.jpg)

3. Ctrl + Right Click one of the addresses.
   
![Alt text](link.jpg)

4. Clicking the link (address) will open up the application in your default browser.

![Alt text](webapp.jpg)

5. If you made it this far, congrats! Here's a 🍪❤️