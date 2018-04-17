---
title: Функции ловушек отчетов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7de5ae8611a3577902d5a6a893d7971ac40cc88b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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