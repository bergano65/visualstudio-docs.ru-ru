---
title: Настройка удаленной службы R в Linux
description: Узнайте, как настроить удаленную службу R в Ubuntu и подсистемах Windows для Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 586f3038ff4bb091fb99160d7965ad927eda070a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851820"
---
# <a name="remote-r-service-for-linux"></a>Удаленная служба R для Linux

Удаленная служба R для Linux сейчас упакована как управляющая программа rtvs-daemon. Управляющая программа поддерживается и протестирована на компьютерах и серверах с Ubuntu 16.04 и 16.10 LTS, а также в Ubuntu на базе подсистемы Windows для Linux. Значительная часть этой статьи содержит инструкции по настройке удаленной службы R в этих системах.

После настройки удаленного компьютера выполните следующие действия, чтобы подключить инструменты R для Visual Studio (RTVS) к этой службе:

1. Выберите **Инструменты R** > **Windows** > **Рабочие области**, чтобы открыть окно **Рабочие области**.
1. Выберите **Добавить подключение**.
1. Задайте имя подключения и укажите его URL-адрес, например `https://localhost:5444` (подсистема Windows для Linux) или `https://public-ip:5444` (контейнер Azure). По завершении щелкните **Сохранить**.
1. Выберите значок подключения или дважды щелкните элемент подключения.
1. Введите учетные данные для входа. Перед именем пользователя должно стоять `<<unix>>\`, например: `<<unix>>\ruser1` (это необходимо для всех подключений к удаленным компьютерам с ОС Linux).
1. Если вы используете самозаверяющий сертификат, может появиться предупреждение. В сообщении будут представлены инструкции, как устранить связанные с предупреждением проблемы.

## <a name="set-up-remote-r-service"></a>Настройка удаленной службы R

Этот раздел описывает следующие варианты:

- [Физический компьютер с Ubuntu](#physical-ubuntu-computer)
- [Виртуальная машина Ubuntu Server или виртуальная машина для обработки и анализа данных в Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Локальный или удаленный контейнер Docker (чистая сборка)](#local-or-remote-docker-container-clean-build)
- [Контейнер, запущенный в экземплярах контейнеров Azure](#container-running-on-azure-container-instances)

В каждом случае на удаленном компьютере должен быть установлен один из следующих интерпретаторов R:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R для Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Физический компьютер с Ubuntu

1. После входа на компьютер загрузите архив Tarball "rtvs-daemon":

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Запустите сценарий установки:

    ```bash
    sudo ./rtvs-install
    ```

    Для автоматической установки используйте `sudo ./rtvs-install -s`.

1. Включите и запустите службу:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Настройте SSL-сертификат (требуется для рабочей среды). По умолчанию rtvs-daemon использует `ssl-cert-snakeoil.pem` и `ssl-cert-snakeoil.pem`, созданные пакетом `ssl-cert`. Во время установки они объединяются в `ssl-cert-snakeoil.pfx`. Для рабочей среды используйте SSL-сертификат, предоставленный вашим администратором. Для настройки SSL-сертификата можно использовать *PFX*-файл и необязательный пароль для импорта в */etc/rtvs/rtvsd.config.json*.

1. Проверьте, что служба работает (необязательно):

    ```bash
    ps -A -f | grep rtvsd
    ```

    Если вы не видите запущенный процесс с именем пользователя `rtvssvc`, запустите его следующей командой:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Сведения о дальнейшей настройке rtvs-daemon см. в разделе `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Виртуальная машина Ubuntu Server или виртуальная машина для обработки и анализа данных в Azure

#### <a name="create-a-vm"></a>Создание виртуальной машины

1. Войдите на [портал Azure](https://portal.azure.com).
1. Перейдите к виртуальным машинам и выберите **Добавить**.
1. В списке доступных образов виртуальных машин найдите и выберите один из следующих вариантов:
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - Виртуальная машина для обработки и анализа данных: `Linux Data Science` (дополнительные сведения см. в разделе [Виртуальные машины для обработки и анализа данных](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/))
1. Задайте модель развертывания `Resource manager` и выберите **Создать**.
1. Укажите имя виртуальной машины, задайте имя пользователя и пароль (пароль является обязательным, так как вход с помощью открытого ключа SSH не поддерживается).
1. Внесите другие необходимые изменения в конфигурацию виртуальной машины.
1. Выберите размер виртуальной машины, проверьте конфигурацию и щелкните **Создать**. После создания виртуальной машины переходите к следующему разделу.

#### <a name="configure-the-vm"></a>Настройка виртуальной машины

1. В разделе виртуальной машины **Сеть** добавьте 5444 как разрешенный входящий порт. Чтобы использовать другой порт, измените параметр в файле конфигурации управляющей программы RTVS ( */etc/rtvs/rtvsd.config.json*).
1. Задайте DNS-имя; вы можете также использовать IP-адрес (необязательно).
1. Подключитесь к виртуальной машине с помощью клиента SSH, например PuTTY для Windows.
1. Следуйте инструкциям для [физического компьютера с Ubuntu](#physical-ubuntu-computer), приведенным выше.

### <a name="windows-subsystem-for-linux-wsl"></a>Подсистема Windows для Linux (WSL)

1. Следуйте инструкциям по установке WSL для [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) или [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Запустите Bash в Windows и следуйте приведенным ранее инструкциям для [физического компьютера с Ubuntu](#physical-ubuntu-computer) с одним исключением. В шаге 3 запустите службу с помощью команды `rtvsd`, так как WSL сейчас не поддерживает интерфейсы systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Локальный или удаленный контейнер Docker (чистая сборка)

1. Создайте файл Docker с указанным ниже содержимым, который установит управляющую программу удаленной службы R и последнюю версию R. **Примечание**. Этот сценарий создает пользователя с именем "ruser1" и паролем "foobar". Вы можете изменить их в двух последних операторах `RUN`.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Выполните сборку файла Docker и запустите его:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Чтобы подключиться к контейнерам из RTVS, используйте путь `https://localhost:5444`, имя пользователя `<<unix>>\ruser1` и пароль `foobar`. Если контейнер запускается на удаленном компьютере, используйте путь `https://remote-host-name:5444`. Порт можно изменить путем обновления файла */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Контейнер, запущенный в экземплярах контейнера Azure

1. Следуйте указаниям раздела [Локальный или удаленный контейнер Docker (чистая сборка)](#local-or-remote-docker-container-clean-build), чтобы создать образ.
1. Отправьте контейнер в центр Docker или репозиторий контейнеров Azure.
1. Запустите Azure CLI и войдите с помощью команды `az login`.
1. Используйте команду `az container create`, чтобы создать контейнер, и введите `--command-line "rtvsd"`, если вы не настроили контейнер для запуска `rtvsd` как службы `systemd`. В команде ниже ожидается, что образ будет в центре Docker. Вы также можете использовать репозиторий контейнеров Azure, добавив в командную строку аргументы с его учетными данными.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Используйте команду `az container list`, чтобы проверить состояние. Вам нужно найти `provisioningState`: `Succeeded`.
1. Если подготовка выполнена, вы сможете подключиться к контейнеру. Найдите общедоступный IP-адрес в поле `ipAddress` и используйте его с учетными данными в файле Docker, чтобы подключиться к контейнеру из RTVS.
