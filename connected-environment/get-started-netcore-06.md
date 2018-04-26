---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке — шаг 6 — сведения о коллективной разработке | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Начало работы в подключенной среде с .NET Core

Предыдущий шаг: [вызов другого контейнера](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Посмотрим на это в действии.
1. Перейдите в окно VS Code для `mywebapi` и внесите изменения в метод `string Get(int id)`, например:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Вперед](get-started-netcore-07.md)
