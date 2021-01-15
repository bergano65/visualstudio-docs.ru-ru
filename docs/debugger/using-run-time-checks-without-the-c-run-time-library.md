---
title: Использование проверки кода во время выполнения без библиотеки среды выполнения C | Документация Майкрософт
description: Вы можете осуществлять компоновку программы без библиотеки времени выполнения C с помощью /NODEFAULTLIB. В таком случае, если вы хотите использовать проверки во время выполнения, необходимо выполнять компоновку с использованием RunTmChk.lib.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfa83533b1ae929bf443dd6c3eb7f7dc3e7db165
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150864"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Использование проверки кода во время выполнения без библиотеки среды выполнения C
Если компоновка осуществляется без библиотеки времени выполнения языка C (с помощью **/NODEFAULTLIB**) и при этом необходимо использовать проверки времени выполнения, нужно осуществлять компоновку с RunTmChk.lib.

`_RTC_Initialize` инициализирует программу для осуществления проверок во время выполнения. Если компоновка осуществляется без библиотеки времени выполнения языка C, перед вызовом `_RTC_Initialize` необходимо проверить, компилируется ли программа с проверками во время выполнения:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Если не осуществлять компоновку с библиотекой времени выполнения C, то необходимо определить функцию с именем `_CRT_RTC_INITW`. `_CRT_RTC_INITW` устанавливает пользовательскую функцию как используемую по умолчанию функцию сообщений об ошибках, как показано ниже:

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

После установки функции сообщения об ошибках по умолчанию можно установить дополнительные функции, сообщающие об ошибках, с помощью `_RTC_SetErrorFuncW`. Дополнительные сведения см. в разделе [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>См. также
[Практическое руководство. Настройка проверок во время выполнения машинного кода](../debugger/how-to-use-native-run-time-checks.md)
