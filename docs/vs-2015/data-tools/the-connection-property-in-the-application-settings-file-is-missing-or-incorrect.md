---
title: Свойство Connection в файле параметров приложения отсутствует или имеет неверный параметр | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b51ff1b20f197de5b6773413558b7e71764780b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655404"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Свойство подключения в файле параметров приложения отсутствует или неверно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Свойства соединения в файле настройки приложения пропущены или неверны. Строка подключения из DBML-файла использовалась на его месте.

 DBML-файл содержит ссылку на строку подключения в файле параметров приложения, который не может быть найден. Это сообщение является информационным; установка строки подключения будет создана при нажатии кнопки **OK**.

### <a name="to-respond-to-this-message"></a>Ответ на данное сообщение

- Нажмите кнопку **ОК**. Информация о подключении, которая содержится в DBML-файле, добавляется к параметрам настройки приложения.

## <a name="see-also"></a>См. также раздел
 Пошаговое руководство [по LINQ to SQL инструментов в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [. Создание классов LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [NIB: Практическое руководство. добавление и удаление параметров приложения](https://msdn.microsoft.com/a233965c-126d-46ab-add4-efb758f576f4) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
