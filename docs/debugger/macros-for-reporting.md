---
title: Макросы для отчетов | Документация Майкрософт
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731389"
---
# <a name="macros-for-reporting"></a>Макросы для создания отчетов
Для отладки можно использовать макросы **_RPTn** и **_RPTFn** , определенные в Crtdbg. H, чтобы заменить использование инструкций `printf`. Их не нужно закрывать в **#ifdef**s, так как они автоматически исчезают в сборке выпуска, когда **_DEBUG** не определен.

|Макрос|Описание|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Выводит строку сообщения и от нуля до четырех аргументов. Для макросов с _RPT1 по **_RPT4** строка сообщения служит в качестве строки формата printf-style для аргументов.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Действуют аналогично макросам **_RPTn**, но дополнительно выводят имя файла и номер строки, где расположен макрос.|

 Рассмотрим следующий пример.

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Этот код выводит значения `someVar` и `otherVar` в **stdout**. Вызов `_RPTF2` можно применить для отчета об этих значениях плюс имя файла и номер строки:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Может оказаться, что конкретному приложению требуется отладка, сообщающая, что макросы, предоставленные библиотекой времени выполнения C, не предоставляют. В таких случаях можно написать макрос, разработанный специально в соответствии с собственными требованиями. Например, в один из файлов заголовка можно включить код для определения макроса с именем **ALERT_IF2**:

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

 Один вызов **ALERT_IF2** может выполнять все функции кода **printf** :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Можно легко изменить пользовательский макрос, чтобы он мог передавать больше или меньше информации в разные места назначения. Этот подход особенно полезен при развитии требований к отладке.

## <a name="see-also"></a>См. также
- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
