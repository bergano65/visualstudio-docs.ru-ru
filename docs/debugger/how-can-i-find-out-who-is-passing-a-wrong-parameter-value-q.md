---
title: Как определить, откуда передается неправильное значение параметра? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 7c2f73f94695d43cea29c3f23b1c3a0c74e79f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Как определить, откуда передается неправильное значение параметра?
## <a name="problem-description"></a>Описание проблемы  
 Одной из функций передается неправильное значение параметра. Эта функция вызывается по всей программе. Как определить, откуда передается неправильное значение?  
  
## <a name="solution"></a>Решение  
  
#### <a name="to-resolve-this-problem"></a>Устранение неполадки  
  
1.  Установите точку останова в начале функции.  
  
2.  Щелкните правой кнопкой мыши точку останова и выберите **условие**.  
  
3.  В **условие точки останова** диалоговое окно, нажмите кнопку **условие** флажок. В разделе [дополнительные точки останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Введите в текстовое поле выражение, например `Var==3`, где `Var` представляет собой имя параметра, который содержит неправильное значение, а `3` — это неправильное значение, переданное параметру.  
  
5.  Выберите **имеет значение True** переключатель и нажмите кнопку **ОК** кнопки.  
  
6.  Запустите программу повторно. Точка останова заставит программу прервать выполнение на начале функции, когда параметр `Var` получит значение `3`.  
  
7.  Затем в окне "Стек вызовов" можно найти вызывающую функцию, чтобы перейти к ее исходному коду. Дополнительные сведения см. в разделе [как: использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Точки останова](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)