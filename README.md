A simple flask app to remove the background of an image with [Rembg](https://github.com/danielgatis/rembg)

Based on https://github.com/codediodeio/rembg-webapp-tutorial with some modifications

Notes:

    uploading files larger than 100mb (u2net.onnx) to GH repo will require git lfs: (not working)

    1. https://git-lfs.com/
    2. https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage

    Therefore download the file from: https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx

## Run it

```
pip install -r requirements.txt
python app.py
```


### To run on ARM architecture, override Dockerfile content:

# FROM python:3.9

# Using Python Slim
# FROM python:3.9-slim
FROM python:3.8-slim


# download this https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx
# copy model to avoid unnecessary download
COPY u2net.onnx /home/.u2net/u2net.onnx

WORKDIR /app

COPY requirements.txt .

# MultiPlatform Requirements

# Install core dependencies.
RUN apt-get update && apt-get install -y libpq-dev build-essential

# Install cmake Manually
RUN apt-get install cmake -y

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5100

CMD ["python", "app.py"]
