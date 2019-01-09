---
title: Узнайте, кто передается неправильное значение параметра | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ffcff71a8897796d64c608df698932da4fd9774f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988100"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Как определить, откуда передается неправильное значение параметра?
## <a name="problem-description"></a>Описание проблемы  
 Одной из функций передается неправильное значение параметра. Эта функция вызывается по всей программе. Как определить, откуда передается неправильное значение?  
  
## <a name="solution"></a>Решение  
  
#### <a name="to-resolve-this-problem"></a>Устранение неполадки  
  
1.  Установите точку останова в начале функции.  
  
2.  Щелкните правой кнопкой мыши точку останова и выберите пункт **Условие**.  
  
3.  В диалоговом окне **Условие для точек останова** установите флажок **Условие**. См. в разделе [дополнительные точки останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Введите в текстовое поле выражение, например `Var==3`, где `Var` представляет собой имя параметра, который содержит неправильное значение, а `3` — это неправильное значение, переданное параметру.  
  
5.  Установите переключатель в положение **верно** и нажмите кнопку **ОК**.  
  
6.  Запустите программу повторно. Точка останова заставит программу прервать выполнение на начале функции, когда параметр `Var` получит значение `3`.  
  
7.  Затем в окне "Стек вызовов" можно найти вызывающую функцию, чтобы перейти к ее исходному коду. Дополнительные сведения см. в разделе [Как использовать окно "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Точки останова](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)