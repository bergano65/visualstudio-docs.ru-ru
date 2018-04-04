---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке с Visual Studio — шаг 4 — отладка контейнера в Kubernetes | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 9b3aa6b0f710707800ea9a1f0533b0c37681ea05
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Начало работы в подключенной среде с .NET Core и Visual Studio

Предыдущий шаг: [создание среды разработки в Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Отладка контейнера в Kubernetes
Когда среда разработки будет создана, вы сможете выполнить отладку приложения. Установите точку останова в коде, например в строке 20 в файле `HomeController.cs`, где задана переменная `Message`. Нажмите клавишу **F5**, чтобы начать отладку. 

Visual Studio будет взаимодействовать со средой разработки для сборки и развертывания приложения, а затем откроет браузер с выполняющимся веб-приложением. Может показаться, что контейнер выполняется локально, но фактически он выполняется в нашей среде разработки в Azure. В адресе указано localhost, поскольку подключенная среда создает временный туннель SSH к контейнеру, выполняющемуся в Azure.

Нажмите на ссылку "**About**" в верхней части страницы для запуска точки останова. У вас будет полный доступ к сведениям об отладке, как если бы код выполнялся локально, например стек вызовов, локальные переменные, сведения об исключениях и т. д.

> [!div class="nextstepaction"]
> [Вызов другого контейнера](get-started-netcore-visualstudio-05.md)