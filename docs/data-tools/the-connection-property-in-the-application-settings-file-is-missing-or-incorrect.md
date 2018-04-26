---
title: Свойство подключения в файле параметров приложения отсутствует или неверно
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 857c9436b3a1279671702575d3ab479d9c2282f4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Свойство подключения в файле параметров приложения отсутствует или неверно

Свойства соединения в файле настройки приложения пропущены или неверны. Строка подключения из DBML-файла использовалась на его месте.

DBML-файл содержит ссылку на строку подключения в файле параметров приложения, который не может быть найден. Это сообщение является информационным; будет создана строку подключения, когда **ОК** нажата.

В ответ на данное сообщение, выберите **ОК**. Информация о подключении, которая содержится в DBML-файле, добавляется к параметрам настройки приложения.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)