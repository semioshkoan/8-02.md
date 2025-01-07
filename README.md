# 8-02.md
### Домашнее задание к занятию «Что такое DevOps. СI/СD» - Семиошко Андрей

### Задание 1

**Что нужно сделать:**

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins [golang](https://golang.org/doc/install).
3. Используя свой аккаунт на GitHub, сделайте себе форк [репозитория](https://github.com/netology-code/sdvps-materials.git). В этом же репозитории находится [дополнительный материал для выполнения ДЗ](https://github.com/netology-code/sdvps-materials/blob/main/CICD/8.2-hw.md).
3. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта ```go test .``` и  ```docker build .```.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---

### Решение 1

### Настройки проэкта

![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_130.png)


![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_131.png)


![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_132.png)


![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_133.png)

### Вывод консоли

```
Started by user andrey
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/СI_СD
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/СI_СD/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
 > git rev-list --no-walk da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
[СI_СD] $ /bin/sh -xe /tmp/jenkins10386971338478069508.sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[СI_СD] $ /bin/sh -xe /tmp/jenkins5081110841156443245.sh
+ docker build . -t ubuntu-bionic:8082/hello-world:v13
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/alpine:latest
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 0.6s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.0s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 12.80kB 0.0s done
#7 DONE 0.0s

#8 [stage-1 2/3] RUN apk -U add ca-certificates
#8 CACHED

#9 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#9 CACHED

#10 [builder 3/4] COPY . ./
#10 CACHED

#11 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:b557d233f2384061044689d9d1b72bdcb174d246b539a310e7f0fe50ae4d6689 done
#13 naming to ubuntu-bionic:8082/hello-world:v13 0.0s done
#13 DONE 0.0s
Finished: SUCCESS
```

---

### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---

### Решение 2

### Настройки проэкта

![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_138.png)

### Вывод консоли

```
Started by user andrey
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/zadanie_2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/netology-code/sdvps-materials.git
 > git init /var/lib/jenkins/workspace/zadanie_2 # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git checkout -b master da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	0.001s
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ docker build . -t 127.0.0.1:8082/hello-world:v1
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/alpine:latest
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 2.0s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.0s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 96.03kB 0.0s done
#7 DONE 0.1s

#8 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#8 CACHED

#9 [builder 3/4] COPY . ./
#9 DONE 0.1s

#10 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#10 DONE 1.8s

#11 [stage-1 2/3] RUN apk -U add ca-certificates
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:b557d233f2384061044689d9d1b72bdcb174d246b539a310e7f0fe50ae4d6689 done
#13 naming to 127.0.0.1:8082/hello-world:v1 0.0s done
#13 DONE 0.0s
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

---

### Задание 3

**Что нужно сделать:**

1. Установите на машину Nexus.
1. Создайте raw-hosted репозиторий.
1. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
1. Загрузите файл в репозиторий с помощью jenkins.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---

### Решение 3

### Настройки проэкта

![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_139.png)

![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_140.png)

![imeg](https://github.com/semioshkoan/8-02.md/blob/main/%D0%92%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_141.png)

### Вывод консоли

```
Started by user andrey
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/zadanie_3
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/zadanie_3/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision da5acf7bcb7f437637adf06fbd03a24dc2c8f13e (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D master # timeout=10
 > git checkout -b master da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
Commit message: "branch main, add creds for vagrant box"
 > git rev-list --no-walk da5acf7bcb7f437637adf06fbd03a24dc2c8f13e # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ /usr/local/go/bin/go build .
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] sh
+ curl -u admin:semenlada22 http://127.0.0.1:8081/repository/my-raw-repo/ --upload-file sdvps-materials -v
*   Trying 127.0.0.1:8081...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to 127.0.0.1 (127.0.0.1) port 8081 (#0)
* Server auth using Basic with user 'admin'
> PUT /repository/my-raw-repo/sdvps-materials HTTP/1.1
> Host: 127.0.0.1:8081
> Authorization: Basic YWRtaW46c2VtZW5sYWRhMjI=
> User-Agent: curl/7.81.0
> Accept: */*
> Content-Length: 2243605
> Expect: 100-continue
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 100 Continue
} [65536 bytes data]
* We are completely uploaded and fine
* Mark bundle as not supporting multiuse
< HTTP/1.1 201 Created
< Date: Tue, 07 Jan 2025 22:19:40 GMT
< Server: Nexus/3.76.0-03 (OSS)
< X-Content-Type-Options: nosniff
< Content-Security-Policy: sandbox allow-forms allow-modals allow-popups allow-presentation allow-scripts allow-top-navigation
< X-XSS-Protection: 1; mode=block
< Content-Length: 0
< 

100 2191k    0     0  100 2191k      0  33.7M --:--:-- --:--:-- --:--:-- 33.9M
* Connection #0 to host 127.0.0.1 left intact
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
---
