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