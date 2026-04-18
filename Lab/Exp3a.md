# Experiment: NGINX Deployment Using Different Base Images

## Objective
Deploy NGINX using different Docker base images and compare image size, layers, and usage.

---

## Part 1: Official NGINX Image

```
docker pull nginx:latest
docker run -d --name nginx-official -p 8080:80 nginx
curl http://localhost:8080
```

![Pull nginx:latest](Screenshots/Exp3/L3-P1-a.png)

![Run nginx-official container](Screenshots/Exp3/L3-p1-b.png)

![Curl localhost:8080](Screenshots/Exp3/L3-p1-c.png)

![Nginx Welcome Page in Browser](Screenshots/Exp3/L3-P1-d.png)

---

## Part 2: Ubuntu Base Image

Dockerfile:
```
FROM ubuntu:22.04
RUN apt-get update && \
    apt-get install -y nginx && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

---

## Part 3: Alpine Base Image

Dockerfile:
```
FROM alpine:3.18
RUN apk update && apk add --no-cache nginx
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

---

## Part 4: Image Size and Layer Comparison

---

## Part 5: Using Custom HTML and Cleanup

---

## Result
NGINX was successfully deployed using the official Docker image. The container was run with port mapping (`8080:80`), and the default NGINX welcome page was verified via `curl` and browser access.

---

## Overall Conclusion
This experiment demonstrated deploying NGINX using different Docker base images (official, Ubuntu, Alpine), comparing their sizes and layers, and verifying successful deployment through browser and curl.
