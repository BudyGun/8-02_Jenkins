# Домашнее задание к занятию "Что такое DevOps. СI/СD" - `Чумаков Константин`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1
Что нужно сделать:

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins golang.
3. Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
   
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---

### Задание 3

**Что нужно сделать:**

1. Установите на машину Nexus.
2. Создайте raw-hosted репозиторий.
3. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
4. Загрузите файл в репозиторий с помощью jenkins.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

---
## Дополнительные задания* (со звёздочкой)

Их выполнение необязательное и не влияет на получение зачёта по домашнему заданию. Можете их решить, если хотите лучше разобраться в материале.

---

### Задание 4*

Придумайте способ версионировать приложение, чтобы каждый следующий запуск сборки присваивал имени файла новую версию. Таким образом, в репозитории Nexus будет храниться история релизов.

Подсказка: используйте переменную BUILD_NUMBER.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Задание 1  Решение

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.

Установлено по инструкции:
```
sudo apt-get install default-jre
```
```
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key |
sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```


![Установка Jenkins](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/jenkins-install.png)
![Установка Jenkins](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/jenkins-install2.png)
![Установка Jenkins2](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/main-jenkins.png)
![Установка Jenkins2](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/jenkins-start.png)

2. Установите на машину с jenkins golang.

использую команды:
```
sudo apt update
sudo apt install golang
go version
```

![Установка golang](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/jenkins-golang.png)

3. Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.

Выполнен fork данного репозитория к себе. Репозиторий доступен по адресу:
```
https://github.com/BudyGun/sdvps-materials.git
```


4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

изменен файл 
```
/etc/hosts
```

добавлена в днс инфо по машине: 
```
10.0.2.15  ubuntu-bionic
```
Установлен докер на машине, пользователь добален в группу докера.

изменены настройки безопасности, изменен файл:
```
sudo nano /etc/docker/daemon.json
```
 В моем  случае он был пустой, создал там строки следующего содержания:

```
{
  "insecure-registries" : ["ubuntu-bionic:8082"]
}
```

Даны права доступа всем на докер:
```
sudo chmod 666 /var/run/docker.sock
```


Перезапущены службы докера и дженкинса:
```
sudo systemctl restart docker.service
sudo sysytemctl restart jenkins.service
```


![Установка Jenkins2](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j10.png)
![Установка Jenkins2](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j11.png)
![Установка Jenkins2](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j12.png)


### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
![Новый проект](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/g23.png)
   
3. Перепишите сборку из задания 1 на declarative в виде кода.
```
pipeline {
    agent any
    stages {
        stage ('Git') {
         steps { git 'https://github.com/BudyGun/sdvps-materials.git'}
        }
        stage ('Test') {
         steps {
             sh '/usr/bin/go test .'
         }
        }
        stage ('Build') {
            steps {
                sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
            }
        }
    }
}
```

![Новый проект](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/g20.png)

В моем случае сборка не собиралась, изменил ветку репозитория в github с main на master, выдавало ошибку:
![Новый проект](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/g24.png)
![Новый проект](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/g22.png)

Результат сборки
![Новый проект](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/g21.png)

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Задание 3

1. Установите на машину Nexus.

Установил с помощью докер контейнера по инструкции с сайта:
https://habr.com/ru/companies/first/articles/661465/

![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j30.png)

2. Создайте raw-hosted репозиторий.

Создал raw-hosted репозиторий my-nexus-repo/

http://192.168.1.6:8081/repository/my-nexus-repo/

![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j40.png)
![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j41.png)

3. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
4. Загрузите файл в репозиторий с помощью jenkins.

код:
```
pipeline {
    agent any
    stages {
        stage ('Git') {
         steps { git 'https://github.com/BudyGun/sdvps-materials.git'}
        }
        stage ('Test') {
         steps {
             sh '/usr/bin/go test .'
         }
        }
        stage ('Build') {
            steps {
                sh '/usr/bin/go build -a  -installsuffix nocgo'
            }
        }
        stage ('Push') {
            steps {
                sh 'curl -u admin:admin http://192.168.1.6:8081/repository/my-nexus-repo/ --upload-file sdvps-materials'
            }        
        }
    }
}
```


![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/d1.png)
![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/d2.png)
![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/d3.png)

Проверка загруженного репозитория в нексус:
![nexus](https://github.com/BudyGun/8-02_Jenkins/blob/master/img/j100.png)

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

   





