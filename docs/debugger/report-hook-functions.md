---
title: Функции ловушек отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 97d39a171d812915a1cf3c1c6450c73098067949
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284202"
---
# <a name="report-hook-functions"></a>Отчетные функции-ловушки
Отчетные функции-ловушки, установленные с помощью [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), вызывается каждый раз [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) создает отчет отладки. Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа. Отчетная функция-ловушка должна иметь следующий прототип:  
  
```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Указатель, передаваемый **_CrtSetReportHook** имеет тип **_CRT_REPORT_HOOK**, как определено в CRTDBG. H:  
  
```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Если библиотека CRT вызывает функцию-ловушку, *nRptType* аргумент содержит категорию отчета (**_CRT_WARN**, **_CRT_ERROR**, или **_CRT Макросы _ASSERT**), *szMsg* содержит указатель на полностью собранную строку отчетного сообщения, и *retVal* указывает ли `_CrtDbgReport` следует продолжить обычное выполнение После создания отчета или запустите отладчик. (Объект *retVal* нулевое значение позволяет продолжить выполнение, а значение 1 запускает отладчик.)  
  
 Если ловушка обрабатывает сообщение полностью, дальнейшая выдача отчета не требуется, он должен вернуть **TRUE**. Если он возвращает **FALSE**, `_CrtDbgReport` вернет сообщение обычным образом.  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
