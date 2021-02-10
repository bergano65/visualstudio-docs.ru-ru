---
title: Макросы для создания отчетов | Документация Майкрософт
description: Сведения о макросах отладки _RPTn и _RPTFn, представленных в CRTDBG.H, и о создании собственных макросов отладки.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0356f05c3f0dac636813d1632f628dd02dd28923
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893130"
---
# <a name="macros-for-reporting"></a>Макросы для создания отчетов
Макросы **_RPTn** и **_RPTFn** (определенные в CRTDBG.H) можно использовать для отладки вместо операторов `printf`. Их не обязательно заключать в **#ifdef**, так как эти макросы в окончательной версии построения автоматически исчезают, если не определен **_DEBUG**.

|Макрос|Описание|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Выводит строку сообщения и от нуля до четырех аргументов. Для макросов с **_RPT1** по **_RPT4** строка сообщения служит в качестве строки формата printf-style для аргументов.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Действуют аналогично макросам **_RPTn**, но дополнительно выводят имя файла и номер строки, где расположен макрос.|

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

Может оказаться, что для отладки конкретного приложения нужна отладочная информация, которую макрос CRT не предоставляет. В таком случае можно написать свой собственный макрос, удовлетворяющий конкретным требованиям. Например, в один из файлов заголовка можно включить код для определения макроса с именем **ALERT_IF2**:

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

 Один вызов макроса **ALERT_IF2** может выполнить все функции кода **printf**.

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Пользовательский макрос можно легко настроить для передачи большего или меньшего объема информации в разные места назначения. Этот подход может особенно пригодиться в случае изменения требований к отладке.

## <a name="see-also"></a>См. также
- [Методы отладки CRT](../debugger/crt-debugging-techniques.md)
