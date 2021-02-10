---
title: Отчетные функции-ловушки | Документация Майкрософт
description: Сведения о функциях-ловушках в Visual Studio. Отчетные функции-ловушки, установленные с помощью _CrtSetReportHook, вызываются каждый раз при создании отчета отладки _CrtDbgReport.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb1e6d2fcd3ec5a2e2c1d784724b17298f0b3e84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891336"
---
# <a name="report-hook-functions"></a>Отчетные функции-ловушки
Отчетные функции-ловушки, установленные с помощью [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), вызываются каждый раз при создании отчета отладки [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw). Помимо всего прочего их можно использовать для фильтрации отчетов, которые позволяют отобрать выделения конкретного типа. Отчетная функция-ловушка должна иметь следующий прототип:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 Указатель, передаваемый **_CrtSetReportHook**, имеет тип **_CRT_REPORT_HOOK**, как определено в CRTDBG.H.

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Когда CRT вызывает функцию-ловушку, аргумент *nRptType* содержит категорию отчета ( **_CRT_WARN**, **_CRT_ERROR** или **_CRT_ASSERT**), *szMsg* содержит указатель на полностью собранную строку отчетного сообщения, а *retVal* задает значение, определяющее поведение `_CrtDbgReport`, которое может продолжить обычное выполнение после создания отчета или запустить отладчик. (Значение *retVal*, равное нулю, позволяет продолжить выполнение, а значение 1 запускает отладчик.)

 Если ловушка полностью обрабатывает сообщение и дальнейшая выдача отчета не требуется, она возвращает значение **TRUE**. Если возвращается значение **FALSE**, `_CrtDbgReport` будет дальше выдавать отчетные сообщения в обычном режиме.

## <a name="see-also"></a>См. также
- [Написание функций отладочных ловушек](../debugger/debug-hook-function-writing.md)
- [Пример crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
