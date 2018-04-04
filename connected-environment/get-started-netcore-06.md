---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке — шаг 6 — сведения о коллективной разработке | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
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
