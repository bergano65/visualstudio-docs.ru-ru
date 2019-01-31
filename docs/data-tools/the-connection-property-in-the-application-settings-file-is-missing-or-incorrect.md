---
title: Свойство подключения в файле параметров приложения отсутствует или неверно
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: d125c5e12320f0c2a17e12c53ca62764f4dfe79f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070826"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Свойство подключения в файле параметров приложения отсутствует или неверно

Свойства соединения в файле настройки приложения пропущены или неверны. Строка подключения из *DBML*-файла использовалась на его месте.

*DBML*-файл содержит ссылку на строку подключения в файле параметров приложения, который не может быть найден. Это сообщение является информационным; установка строки подключения будет создана при нажатии кнопки **OK**.

Чтобы ответить на это сообщение, выберите **ОК**. Информация о подключении, которая содержится в *DBML*-файле, добавляется к параметрам настройки приложения.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)