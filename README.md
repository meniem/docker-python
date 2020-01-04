# JSON to XML converter, encryption and transfer to AWS S3 using Python

The repo consiits of two Python scripts, the first one converts JSON files to XML, encrypt the converted file, and transfer it to Amazon S3 bucket. While the second one is downloading the file from the S3 bucket, decrypt it, and save it on a directory called “XML”.

> The 2 scripts are built using a Docker image which is based on Python-Slim image and has all the dependencies needed to run the script, such as: Boto3, dict2xml and pyDes. The Docker image will also copy all the necessary files from the current directory to the image, and then it will execute the Python script from the Home directory.


# Prerequisites:
 - Docker.
 - Python3.
 - Python3 modules: Boto3 pyDesc, dict2xml and bz2.
 - AWS S3 bucket, and an account that has a write access to it.


# Installation Steps:

clone the repo

build the first container
```sh
docker build -t python_encrypt ./01_python_encrypt
```

The first Docker image will do the below steps:
 - Function 1: Read the JSON file from the JSON directory Convert to XML
 - Function 2: Encrypt the XML file
 - Execute the 2 functions to convert and encrypt the file
 - Upload the encrypted file to S3 bucket

build the first container
```sh
docker build -t python_decrypt ./02_python_decrypt
```

 - The second Docker image will do the below steps:
 - The decryption function.
 - Download the encrypted file from S3 bucket
 - Execute the above function to decrypt the file and store it locally in xml directory.
