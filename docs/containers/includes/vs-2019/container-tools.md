---
title: Использование средств Visual Studio для Docker с ASP.NET Core
author: ghogen
description: Сведения об использовании средств Visual Studio 2019 и Docker для Windows
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: d0da02773913a610c77d7165fdb0f9becfc59e9c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75928002"
---
В Visual Studio можно легко выполнять сборку, отлаживать и запускать контейнерные приложения .NET, ASP.NET и ASP.NET Core и публиковать их в реестре контейнеров Azure (ACR), Docker Hub, службе приложений Azure или собственном реестре контейнеров. В этой статье рассматривается публикация приложения ASP.NET Core в реестре контейнеров Azure (ACR).

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой **Веб-разработка**, **Средства Azure** и (или) **Кроссплатформенная разработка .NET Core**.
* [Средства разработки .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) для разработки с использованием .NET Core 2.2.
* Для публикации в Реестр контейнеров Azure требуется подписка Azure. [Зарегистрируйтесь для получения бесплатной пробной версии](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="installation-and-setup"></a>Установка и настройка

Чтобы установить Docker, сначала ознакомьтесь с разделом [Docker для Windows: что следует знать перед установкой](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Затем установите [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="add-a-project-to-a-docker-container"></a>Добавление проекта в контейнер Docker

1. Создайте проект, используя шаблон **Веб-приложение ASP.NET Core**.
1. Выберите **Веб-приложение** и установите флажок **Включение поддержки Docker**.

   ![Флажок "Включение поддержки Docker"](../../media/container-tools/vs-2019/create-new-web-application.PNG)

1. Выберите нужный тип контейнера (Windows или Linux) и нажмите кнопку **Создать**.

## <a name="dockerfile-overview"></a>Общие сведения о Dockerfile

*Dockerfile* с инструкциями по созданию окончательного образа Docker создается в проекте. См. [справочник по Dockerfile](https://docs.docker.com/engine/reference/builder/) для получения сведений о других доступных в нем командах.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

Предыдущий *Dockerfile* основан на образе [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) и включает в себя инструкции по изменению базового образа путем сборки проекта и добавления его в контейнер.

Если в диалоговом окне создания проекта установлен флажок **Configure for HTTP** (Настроить для трафика HTTPS), *Dockerfile* предоставляет два порта. Один порт используется для трафика HTTP, другой — для HTTPS. Если флажок не установлен, для трафика HTTP предоставляется один порт (80).

## <a name="debug"></a>Отладка

Выберите пункт **Docker** в раскрывающемся списке отладки на панели инструментов, чтобы начать отладку приложения. Может появиться сообщение с запросом о доверии сертификату. Выберите доверие сертификату, чтобы продолжить.

В параметре **Инструменты контейнера** в окне **Вывод** показано, какие действия выполняются.

## <a name="containers-window"></a>Окно "Контейнеры"

В Visual Studio 2019 версии 16.4 или более поздних версиях окно **Контейнеры** можно использовать для просмотра запущенных на компьютере контейнеров, а также доступных образов.

Откройте окно **Контейнеры**, используя поле поиска в интегрированной среде разработки (нажмите сочетание клавиш **CTRL**+**Q**), введите `container` и в списке выберите **Контейнеры**.

Окно **Контейнеры** можно закрепить в удобном месте, например под редактором. Для этого перетащите его и следуйте инструкциям по размещению.

В окне найдите контейнер и перейдите по вкладкам, чтобы просмотреть переменные среды, сопоставления портов, журналы и файловую систему.

![Снимок экрана: окно "Контейнеры"](../../media/overview/vs-2019/container-tools-window.png)

Дополнительные сведения см. в статье [Сведения о просмотре и диагностике контейнеров и образов в Visual Studio](../../view-and-diagnose-containers.md).

## <a name="publish-docker-images"></a>Публикация образов Docker

После завершения цикла разработки и отладки приложения можно создать рабочий образ приложения.

1. Выберите в раскрывающемся списке конфигурации значение **Выпуск** и выполните сборку приложения.
1. В **обозревателе решений** щелкните правой кнопкой проект и выберите **Опубликовать**.
1. В диалоговом окне целевой публикации выберите вкладку **Реестр контейнеров**.
1. Выберите **Создать реестр контейнеров Azure** и щелкните **Опубликовать**.
1. Заполните нужные значения в окне **Создать новый реестр контейнеров Azure**.

    | Параметр      | Рекомендуемое значение  | Описание                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-префикс** | Глобально уникальное имя | Имя, которое однозначно идентифицирует реестр контейнеров. |
    | **Подписка** | Выберите свою подписку | Подписка Azure, которую нужно использовать. |
    | **[Группа ресурсов](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Имя группы ресурсов, в которой создается реестр контейнеров. Чтобы создать группу ресурсов, выберите **Создать**.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Стандартный | Уровень обслуживания в реестре контейнеров  |
    | **Расположение реестра** | Расположение рядом с вами | Выберите расположение в ближайшем [регионе](https://azure.microsoft.com/regions/) или в регионе, расположенном рядом с другими службами, которые будут использовать реестр контейнеров. |

    ![Диалоговое окно "Создание реестра контейнеров Azure" Visual Studio][0]

1. Нажмите кнопку **Создать**.

   ![Снимок экрана с сообщением об успешной публикации](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Следующие шаги

Теперь можно извлечь контейнер из реестра в любой узел, поддерживающий работу образов Docker, например [Экземпляры контейнеров Azure](/azure/container-instances/container-instances-tutorial-deploy-app).

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
