# docker-compose-v2

Установка Docker Compose из GitHub
Для этой операции в вашей системе должны быть установлены curl и wget. И, конечно же, вам нужен доступ к Терминалу как пользователю с правами sudo.

sudo apt update

    sudo apt install -y curl wget
    
После установки curl загрузите последнюю версию Compose на свой компьютер с Linux.

    curl -s https://api.github.com/repos/docker/compose/releases/latest | grep browser_download_url  | grep docker-compose-linux-x86_64 | cut -d '"' -f 4 | wget -qi -
    
Сделайте двоичный файл исполняемым.

    chmod +x docker-compose-linux-x86_64
    
Переместите файл по вашему ПУТИ.

    sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose
      На debian11 - /usr/bin/docker-compose
Подтвердите версию.

    $ docker-compose version
Docker Compose version v2.28.1

Добавить пользователя в группу docker:

    sudo usermod -aG docker $USER
    newgrp docker

Источник: https://dockerhosting.ru/blog/ustanovka-docker-na-debian-12/#Установка_Docker_Compose_из_GitHub



# Update Docker 

Добавление репозитория docekr и его обновление

Всё делалось на debian12 


      echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
      install -m 0755 -d /etc/apt/keyrings
      apt-get install gpg -y
      curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
      chmod a+r /etc/apt/keyrings/docker.gpg
      apt-get update
      apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
