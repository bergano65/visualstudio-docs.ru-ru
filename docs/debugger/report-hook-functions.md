---
title: "Функции ловушек отчетов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 958c33c623830af509185b3d35ef8a8b5956aaae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="report-hook-functions"></a>Отчетные функции-ловушки
Отчетные функции-ловушки, установленные с помощью [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), вызывается каждый раз [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) создает отладочный отчет. Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа. Отчетная функция-ловушка должна иметь следующий прототип:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Указатель, передаваемый **_CrtSetReportHook** относится к типу **_CRT_REPORT_HOOK**, как определено в CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Когда библиотеки CRT вызывает функцию-обработчик *nRptType* аргумент содержит категорию отчета (**_CRT_WARN**, **_CRT_ERROR**, или **_CRT _ASSERT**), *szMsg* содержит указатель на строку сообщения полностью собранное отчета и *retVal* указывает ли `_CrtDbgReport` следует продолжить обычное выполнение После создания отчета или запуска отладчика. (A *retVal* нулевое значение продолжает выполнение, а значение 1 запускает отладчик.)  
  
 Если ловушка обрабатывает сообщение полностью, дальнейшая выдача отчета не требуется, он должен возвращать **TRUE**. Если он возвращает **FALSE**, `_CrtDbgReport` будет дальше выдавать отчетные сообщения обычно.  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)