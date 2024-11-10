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
