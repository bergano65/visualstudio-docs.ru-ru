---
title: (Создание исключения)-диалоговое окно отладчика Microsoft Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d2b27620cbc37bd771fff364d06a1a33d9c8b07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571684"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Отладчик Microsoft Visual Studio (создание исключения) - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [диалоговое окно отладчика Microsoft Visual Studio (создание исключения)](https://docs.microsoft.com/visualstudio/debugger/microsoft-visual-studio-debugger-exception-thrown-dialog-box).  
  
В программе возникло исключение. Это диалоговое окно сообщает о типе вызванного исключения. В коде должна быть предусмотрена обработка этого исключения. Для обработки исключения можно выбрать один из следующих вариантов:  
  
 **Break**  
 Разрешает передать выполнение в отладчик. До приостановки выполнения обработчик исключения не вызывается. Если продолжить выполнение после приостановки, будет вызван обработчик исключения.  
  
 **Continue**  
 Разрешает продолжить выполнение, давая возможность обработчику исключения обработать исключение. Этот вариант недоступен для определенных типов исключений. **По-прежнему** позволит продолжить выполнение приложения. В случае приложения в машинном коде это приведет к повторному вызову исключения. В случае управляемого приложения либо произойдет завершение программы, либо исключение будет обработано главным приложением.  
  
> [!NOTE]
>  После возникновения необрабатываемого исключения в управляемом коде продолжение выполнения невозможно. Выбор **Продолжить** после необработанного исключения в управляемом коде приведет к остановке отладки.  
  
 **игнорировать**  
 Разрешает продолжить выполнение без вызова обработчика исключения. Поскольку обработчик исключения не вызывается, это может привести к усугублению проблемы, включая возникновение новых исключений и ошибок. Этот вариант недоступен для определенных типов исключений.  
  
## <a name="see-also"></a>См. также  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)   
 [Рекомендации по обработке исключений](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Обработка исключений](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)



