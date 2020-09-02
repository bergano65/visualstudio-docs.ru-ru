---
title: Серверные приложения SDI | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148150"
---
# <a name="sdi-server-applications"></a>Приложения сервера SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В случае проектов C/C++, C# или Visual Basic при отладке приложения SDI-сервера необходимо указать значение `/Embedding` или `/Automation` в свойстве **Аргументы командной строки** диалогового окна "Страницы свойств *Проект*".  
  
 Данные аргументы командной строки позволяют отладчику запустить приложение сервера так, как если бы оно было запущено из контейнера. Если в этот момент запустить контейнер из диспетчера программ или диспетчера файлов, то он будет использовать экземпляр сервера, запущенный в отладчике.  
  
## <a name="finding-the-command-line-arguments-property"></a>Поиск свойства "Аргументы командной строки"  
 Чтобы открыть диалоговое окно "Страницы свойств *Проект*", щелкните правой кнопкой мыши проект в обозревателе решений, а затем выберите пункт "Свойства" в контекстном меню. Чтобы найти свойство "Аргументы командной строки", разверните категорию "Свойства конфигурации" и щелкните страницу "Отладка".  
  
## <a name="see-also"></a>См. также:  
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Практическое руководство. Отладка серверов COM](../debugger/how-to-debug-com-servers.md)
