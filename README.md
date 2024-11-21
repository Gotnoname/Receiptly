### Docker hub
https://hub.docker.com/repository/docker/gotnonamedocker/receiptly

### What is Receiptly?

Receiptly is a free receipt manager. With Receiptly you can effortlessly organize and access your receipts with the web app. Upload pictures of your receipts, tag them, with quick access, and easy searching—all in one place.

### How to use this image

```
$ docker run -d \
  --name receiptly \
  -p 5100:5100 \
  -e ASPNETCORE_URLS="http://+:5100" \
  -e JWT_ISSUER="" \
  -e JWT_SECRET="" \
  -v /path/on/host:/app/Files \
  --restart unless-stopped \
  docker.io/gotnonamedocker/receiptly:latest
```
Then, access it via ```http://localhost:5100``` or ```http://host-ip:5100``` in a browser.

The following environment variables are also used for configuring your Receiptly instance

* ```-e JWT_ISSUER=```
    This is your custom JWT issuer name

* ```-e JWT_SECRET=```
    This is your custom JWT secret value. Generate one here [https://jwtsecret.com/generate].


### Volumes

The data is structured in the Data folder with a Database-folder nad a ReceiptData folder. The ReceiptData folder contains the uploaded data (image, pdf etc).

```
-v /path/on/host:/app/Files
```


### Docker compose

Example ```docker-compose.yml``` for Receiptly:

```
services:
  receiptly:
    image: docker.io/gotnonamedocker/receiptly:latest
    ports:
      - "5100:5100"
    environment:
      ASPNETCORE_URLS: "http://+:5100"
      JWT_ISSUER: "your_custom_issuer_name_here"
      JWT_SECRET: "your_secret_here"
    volumes:
      - /path/on/host:/app/Files
    restart: unless-stopped
```

### License and resources
Receiptly is built using React and dotnet.

* UI components from: https://mui.com/
* Icons from: https://fontawesome.com/
* Toastify: https://fkhadra.github.io/react-toastify/introduction

