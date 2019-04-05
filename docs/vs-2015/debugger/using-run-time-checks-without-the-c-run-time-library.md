---
title: Использование среды выполнения проверки без библиотеки времени выполнения C | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f5d9c56cfde6e87c0f9bd92289597e77bfea875
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978870"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Использование проверки кода во время выполнения без библиотеки среды выполнения C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если при компоновке программы без библиотеки времени выполнения C, с помощью **/NODEFAULTLIB**и необходимо использовать проверки времени выполнения, нужно осуществлять компоновку с RunTmChk.lib.  
  
 `_RTC_Initialize` инициализирует программу для осуществления проверок во время выполнения. Если компоновка осуществляется без библиотеки времени выполнения языка C, перед вызовом `_RTC_Initialize` необходимо проверить, компилируется ли программа с проверками во время выполнения:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Если не осуществлять компоновку с библиотекой времени выполнения C, то необходимо определить функцию с именем `_CRT_RTC_INITW`. `_CRT_RTC_INITW` устанавливает пользовательскую функцию как используемую по умолчанию функцию сообщений об ошибках, как показано ниже:  
  
```  
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
  
 После установки функции сообщения об ошибках по умолчанию можно установить дополнительные функции, сообщающие об ошибках, с помощью `_RTC_SetErrorFuncW`. Дополнительные сведения см. в разделе [_RTC_SetErrorFuncW](http://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка проверок во время выполнения машинного кода](../debugger/how-to-use-native-run-time-checks.md)
