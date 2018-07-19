---
title: Макросы для создания отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b254323fac5d670cd44399cd8d22c9530c4510
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056606"
---
# <a name="macros-for-reporting"></a>Макросы для создания отчетов
Для отладки, можно использовать **_RPTn** и **_RPTFn** макросы, определенные в CRTDBG. H, чтобы заменить использование `printf` инструкций. Не нужно их в inclose **#ifdef**s, так как они автоматически исчезают в выпуске построение **_DEBUG** не определена.  
  
|Макрос|Описание:|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Выводит строку сообщения и от нуля до четырех аргументов. Для макросов _RPT1 **_RPT4**, строка сообщения служит строка форматирования стиле printf для аргументов.|  
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Совпадение с кодом **_RPTn**, но эти макросы также выводят файла имя и номер строки где расположен макрос.|  
  
 Рассмотрим следующий пример.  
  
```cpp
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Этот код выводит значения `someVar` и `otherVar` для **stdout**. Вызов `_RPTF2` можно применить для отчета об этих значениях плюс имя файла и номер строки:  
  
```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
Вы можете обнаружить, что конкретного приложения нужна отладочная информация, не предоставляемый в библиотеке времени выполнения C макрос. В этих случаях можно написать макрос, в частности, в соответствии с вашими требованиями. В одном из файлов заголовка, например, можно включить код для определения макроса с именем **ALERT_IF2**:  
  
```cpp
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Один вызов **ALERT_IF2** сделать все функции **printf** кода:  
  
```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Кроме того, можно легко изменить пользовательский макрос для более или менее передачи сведений в различные назначения. Этот подход особенно полезна при развитии требований отладки.  
  
## <a name="see-also"></a>См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
