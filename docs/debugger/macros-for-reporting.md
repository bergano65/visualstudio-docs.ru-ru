---
title: "Макросы для создания отчетов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn - макрос"
  - "_RPTn - макрос"
  - "CRT - библиотека, макросы для создания отчетов"
  - "отладка [CRT], макросы для создания отчетов"
  - "макросы, CRT макросы для создания отчетов"
  - "макросы, отладка при помощи"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Макросы для создания отчетов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Макросы **\_RPTn** и **\_RPTFn** \(определенные в CRTDBG.H\) можно использовать для отладки вместо операторов `printf`.  Если не определен **\_DEBUG**, эти макросы в окончательной версии построения автоматически исчезают, поэтому их не обязательно заключать в **\#ifdef**.  
  
|Макрос|Описание|  
|------------|--------------|  
|**\_RPT0**, **\_RPT1**, **\_RPT2**, **\_RPT3**, **\_RPT4**|Выводит строку сообщения и от нуля до четырех аргументов.  Для макросов \_RPT1...**\_RPT4** строка сообщения служит в качестве строки формата printf\-style для аргументов.|  
|**\_RPTF0**, **\_RPTF1**, **,\_RPTF2**, **\_RPTF4**|Действуют аналогично макросам **\_RPTn**, но дополнительно выводят имя файла и номер строки, где расположен макрос.|  
  
 Рассмотрим следующий пример:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Этот код выводит значения `someVar` и `otherVar` в **stdout**.  Вызов `_RPTF2` можно применить для отчета об этих значениях плюс имя файла и номер строки:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Если для отладки конкретного приложения нужна отладочная информация, которую макрос CRT не предоставляет, можно написать свой собственный макрос, удовлетворяющий конкретным требованиям.  Например, в один из файлов заголовка можно включить код для определения макроса с именем **ALERT\_IF2**:  
  
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
  
 Один вызов **ALERT\_IF2** может выполнить все функции кода **printf**, описанные в начале этого раздела:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Поскольку пользовательский макрос легко может быть настроен выдавать больше или меньше информации в зависимости от целей и удобства, этот подход может пригодиться в случае изменения требований при отладке.  
  
## См. также  
 [Методы отладки CRT](../debugger/crt-debugging-techniques.md)