---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке с Visual Studio — шаг 4 — отладка контейнера в Kubernetes | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31886196"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Начало работы в подключенной среде с .NET Core и Visual Studio

Предыдущий шаг: [создание среды разработки в Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Отладка контейнера в Kubernetes
Когда среда разработки будет создана, вы сможете выполнить отладку приложения. Установите точку останова в коде, например в строке 20 в файле `HomeController.cs`, где задана переменная `Message`. Нажмите клавишу **F5**, чтобы начать отладку. 

Visual Studio будет взаимодействовать со средой разработки для сборки и развертывания приложения, а затем откроет браузер с выполняющимся веб-приложением. Может показаться, что контейнер выполняется локально, но фактически он выполняется в нашей среде разработки в Azure. В адресе указано localhost, поскольку подключенная среда создает временный туннель SSH к контейнеру, выполняющемуся в Azure.

Нажмите на ссылку "**About**" в верхней части страницы для запуска точки останова. У вас будет полный доступ к сведениям об отладке, как если бы код выполнялся локально, например стек вызовов, локальные переменные, сведения об исключениях и т. д.

> [!div class="nextstepaction"]
> [Вызов другого контейнера](get-started-netcore-visualstudio-05.md)