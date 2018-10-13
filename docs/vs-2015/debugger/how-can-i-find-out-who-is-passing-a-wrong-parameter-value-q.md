---
title: Как определить, откуда передается неправильное значение параметра? | Документы Майкрософт
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
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87d44eeabd3c65d6d86125c4029bfc868a539f8c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207627"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Как определить, откуда передается неправильное значение параметра?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Описание проблемы  
 Одной из функций передается неправильное значение параметра. Эта функция вызывается по всей программе. Как определить, откуда передается неправильное значение?  
  
## <a name="solution"></a>Решение  
  
#### <a name="to-resolve-this-problem"></a>Устранение неполадки  
  
1.  Установите точку останова в начале функции.  
  
2.  Щелкните правой кнопкой мыши точку останова и выберите **условие**.  
  
3.  В **условие точки останова** диалоговое окно, щелкните **условие** "флажок". См. в разделе [дополнительные точки останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Введите в текстовое поле выражение, например `Var==3`, где `Var` представляет собой имя параметра, который содержит неправильное значение, а `3` — это неправильное значение, переданное параметру.  
  
5.  Выберите **имеет значение True** кнопку-переключатель и нажмите кнопку **ОК** кнопки.  
  
6.  Запустите программу повторно. Точка останова заставит программу прервать выполнение на начале функции, когда параметр `Var` получит значение `3`.  
  
7.  Затем в окне "Стек вызовов" можно найти вызывающую функцию, чтобы перейти к ее исходному коду. Дополнительные сведения см. в разделе [как: использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Точки останова](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)



