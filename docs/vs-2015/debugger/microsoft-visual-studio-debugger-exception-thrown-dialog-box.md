---
title: (Создание исключения)-диалоговое окно отладчика Microsoft Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 5c3ce3a3362c657d4302ba919c866d4a32055423
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226171"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Отладчик Microsoft Visual Studio (создание исключения) - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



