---
title: Функции ловушек отчетов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38d553abd50d1b5870adc31e08d349f9f84c0579
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992155"
---
# <a name="report-hook-functions"></a>Отчетные функции-ловушки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отчетные функции-ловушки, установленные с помощью [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), вызываются каждый раз при создании отчета отладки [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc). Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа. Отчетная функция-ловушка должна иметь следующий прототип:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Указатель, передаваемый **_CrtSetReportHook** имеет тип **_CRT_REPORT_HOOK**, как определено в CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Когда CRT вызывает функцию-ловушку, аргумент *nRptType* содержит категорию отчета (**_CRT_WARN**, **_CRT_ERROR** или **_CRT_ASSERT**), *szMsg* содержит указатель на полностью собранную строку отчетного сообщения, а *retVal* задает значение, определяющее поведение `_CrtDbgReport`, которое может продолжить обычное выполнение после создания отчета или запустить отладчик. (Значение *retVal*, равное нулю, позволяет продолжить выполнение, а значение 1 запускает отладчик.)  
  
 Если ловушка полностью обрабатывает сообщение и дальнейшая выдача отчета не требуется, она возвращает значение **TRUE**. Если возвращается значение **FALSE**, `_CrtDbgReport` будет дальше выдавать отчетные сообщения в обычном режиме.  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
