---
title: Создание среды разработки Node.js с контейнерами с помощью Kubernetes в облаке — шаг 6 — сведения о коллективной разработке | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Начало работы в подключенной среде с Node.js

Предыдущий шаг: [вызов службы, запущенной в отдельном контейнере](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Посмотрим на это в действии.
1. Перейдите в окно VS Code для `mywebapi` и внесите изменения в обработчик GET `/` по умолчанию, например:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Вперед](get-started-nodejs-07.md)

