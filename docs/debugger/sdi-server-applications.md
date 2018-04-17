---
title: Приложения сервера SDI | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b61b5797766a69e291c2d3d38500055890169a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sdi-server-applications"></a>Приложения сервера SDI
При отладке приложения SDI-сервера, необходимо указать `/Embedding` или `/Automation` в **аргументы командной строки** свойство в *проекта* диалоговом окне страницы свойств для C/C++, C# или Проекты Visual Basic.  
  
 Данные аргументы командной строки позволяют отладчику запустить приложение сервера так, как если бы оно было запущено из контейнера. Если в этот момент запустить контейнер из диспетчера программ или диспетчера файлов, то он будет использовать экземпляр сервера, запущенный в отладчике.  
  
## <a name="finding-the-command-line-arguments-property"></a>Поиск свойства "Аргументы командной строки"  
 Чтобы получить доступ к *проекта* диалоговое окно страницы свойств, щелкните правой кнопкой мыши проект в обозревателе решений и выберите в контекстном меню пункт Свойства. Чтобы найти свойство "Аргументы командной строки", разверните категорию "Свойства конфигурации" и щелкните страницу "Отладка".  
  
## <a name="see-also"></a>См. также  
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Практическое руководство. Отладка COM-серверов](../debugger/how-to-debug-com-servers.md)