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
ms.openlocfilehash: db0ac06d26e7e597d9f8d4b3c11a9cf8db188e80
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174131"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Свойство подключения в файле параметров приложения отсутствует или неверно

Свойства соединения в файле настройки приложения пропущены или неверны. Строка подключения из *.dbml* файла использовалась на его место.

*.Dbml* файл содержит ссылку на строку подключения в файле параметров приложения, который не удается найти. Это информационное сообщение; будет создана строку подключения, когда **ОК** нажатии.

Чтобы ответить на это сообщение, выберите **ОК**. Сведения о соединении, содержащийся в *.dbml* файл добавляется к параметрам приложения.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)