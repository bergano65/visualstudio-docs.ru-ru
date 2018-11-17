---
title: Функции ловушек отчетов | Документация Майкрософт
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
manager: ghogen
ms.openlocfilehash: d3b7916f729f0d1ea1a254ecde8e5c53ea8b8a51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777265"
---
# <a name="report-hook-functions"></a>Отчетные функции-ловушки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отчетные функции-ловушки, установленные с помощью [_CrtSetReportHook](http://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), вызывается каждый раз [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) создает отчет отладки. Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа. Отчетная функция-ловушка должна иметь следующий прототип:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Указатель, передаваемый **_CrtSetReportHook** имеет тип **_CRT_REPORT_HOOK**, как определено в CRTDBG. H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Если библиотека CRT вызывает функцию-ловушку, *nRptType* аргумент содержит категорию отчета (**_CRT_WARN**, **_CRT_ERROR**, или **_CRT Макросы _ASSERT**), *szMsg* содержит указатель на полностью собранную строку отчетного сообщения, и *retVal* указывает ли `_CrtDbgReport` следует продолжить обычное выполнение После создания отчета или запустите отладчик. (Объект *retVal* нулевое значение позволяет продолжить выполнение, а значение 1 запускает отладчик.)  
  
 Если ловушка обрабатывает сообщение полностью, дальнейшая выдача отчета не требуется, он должен вернуть **TRUE**. Если он возвращает **FALSE**, `_CrtDbgReport` вернет сообщение обычным образом.  
  
## <a name="see-also"></a>См. также  
 [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)   
 [Образец crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



