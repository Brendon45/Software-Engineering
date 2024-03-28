# Welcome to 0x11. Python - Network #1 concepts insight:

## Python

## Scripting

## Back-end

## API

## Most asked questions:

- How to fetch internet resources with the Python package urllib
- How to decode urllib body response
- How to use the Python package requests #requestsiswaysimplerthanurllib
- How to make HTTP GET request
- How to make HTTP POST/PUT/etc. request
- How to fetch JSON resources
- How to manipulate data from an external service

## ANSWERS:

1. Fetching Internet Resources with urllib:

- The urllib.request.urlopen() function is commonly used to access web resources like HTML pages, JSON data, or image files from URLs. For example, fetching the HTML content of a webpage:

python code:

import urllib.request

url = "https://www.example.com"
with urllib.request.urlopen(url) as response:
    html_content = response.read().decode("utf-8")
    print(html_content)

2. Decoding urllib Body Response:

- When using urllib, responses are typically returned as byte strings, which need to be decoded to human-readable text. For instance, decoding JSON data fetched from an API:

python code:

import urllib.request
import json

url = "https://api.example.com/data"
with urllib.request.urlopen(url) as response:
    json_data = json.loads(response.read().decode("utf-8"))
    print(json_data)

3. Using the Python Package requests:

- The requests library offers a more user-friendly interface for making HTTP requests. For instance, fetching JSON data from a REST API:

python code:

import requests

url = "https://api.example.com/data"
response = requests.get(url)
json_data = response.json()
print(json_data)

4. Making HTTP GET Request:

- With requests, making an HTTP GET request is straightforward. For example, fetching the content of a webpage:

python code:

import requests

url = "https://www.example.com"
response = requests.get(url)
print(response.text)

5. Making HTTP POST/PUT/etc. Request:

- requests supports various HTTP methods like POST, PUT, DELETE, etc. For instance, sending data via a POST request:

python code:

import requests

url = "https://api.example.com/update"
data = {"key": "value"}
response = requests.post(url, data=data)
print(response.text)

6. Fetching JSON Resources:

- When dealing with APIs that return JSON data, requests can parse it directly into Python objects. For example:

python code:

import requests

url = "https://api.example.com/data"
response = requests.get(url)
json_data = response.json()
print(json_data)

7. Manipulating Data from an External Service:

After fetching data, you can perform various operations on it, such as filtering, sorting, or analyzing. For instance, processing JSON data fetched from an API:

python code:

import requests

url = "https://api.example.com/data"
response = requests.get(url)
json_data = response.json()

# Extract relevant information
for item in json_data:
    print(item["name"], item["value"])
