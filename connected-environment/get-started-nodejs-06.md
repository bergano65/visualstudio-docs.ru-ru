---
title: Создание среды разработки Node.js с контейнерами с помощью Kubernetes в облаке — шаг 6 — сведения о коллективной разработке | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
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

