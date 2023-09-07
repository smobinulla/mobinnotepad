# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/smobinulla/mobinnotepad.git
```

2. Build the app
```
docker build -t mobinnotepad .
```

3. Run the app
```
docker run -d -p 8050:8000 smobinulla/mobinnotepad:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
