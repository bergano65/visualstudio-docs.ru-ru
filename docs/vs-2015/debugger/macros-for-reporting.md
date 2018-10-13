---
title: Макросы для создания отчетов | Документация Майкрософт
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
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84b5e72b15d085e29823fb8c8e116a153ff550e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224384"
---
# <a name="macros-for-reporting"></a>Макросы для создания отчетов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно использовать **_RPTn**, и **_RPTFn** макросы, определенные в CRTDBG. H, чтобы заменить использование `printf` для отладки. Эти макросы автоматически исчезают в выпуске построение **_DEBUG** не определен, поэтому нет необходимости заключать их в **#ifdef**s.  
  
|Макрос|Описание|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Выводит строку сообщения и от нуля до четырех аргументов. Для макросов _RPT1 **_RPT4**, строка сообщения служит строка форматирования стиле printf для аргументов.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Совпадение с кодом **_RPTn** , но эти макросы также выводят файла имя и номер строки где расположен макрос.|  
  
 Рассмотрим следующий пример.  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Этот код выводит значения `someVar` и `otherVar` для **stdout**. Вызов `_RPTF2` можно применить для отчета об этих значениях плюс имя файла и номер строки:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Если для отладки конкретного приложения нужна отладочная информация, которую макрос CRT не предоставляет, можно написать свой собственный макрос, удовлетворяющий конкретным требованиям. В одном из файлов заголовка, например, можно включить код для определения макроса с именем **ALERT_IF2**:  
  
```  
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
  
 Один вызов **ALERT_IF2** может выполнить все функции **printf** кода в начале этого раздела:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Поскольку пользовательский макрос легко может быть настроен выдавать больше или меньше информации в зависимости от целей и удобства, этот подход может пригодиться в случае изменения требований при отладке.  
  
## <a name="see-also"></a>См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)



