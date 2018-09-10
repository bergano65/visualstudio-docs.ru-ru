---
title: Как определить конкретный вызов функции, приведший к сбою, если таких вызовов было порядка ста? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b552e7a81c43ec67951cac584b215f38f06c12
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284037"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Как определить конкретный вызов функции, приведший к сбою, если таких вызовов было порядка ста?
## <a name="problem-description"></a>Описание проблемы  
 Программа дает сбой при вызове некой функции `CnvtV`. Программа, вероятно, вызывает эту функцию перед сбоем пару сотен раз. Если поставить точку останова на `CnvtV`, программа останавливается на каждом вызове этой функции, а этого не требуется. Непонятно, что приводит к сбойному вызову, поэтому поставить условную точку останова невозможно. Что можно сделать?  
  
## <a name="solution"></a>Решение  
 Можно установить точку останова на функции с **число попаданий** на что он недостижимо большому значению. В этом случае так как вы считаете, что функция `CnvtV` вызывается пару сотен раз, можно задать **число попаданий** 1000 или более. Затем запустить программу и подождать сбоя. Когда сбой произойдет, откройте окно точек останова и просмотрите их список. Точка останова в `CnvtV` появилась, следом появилось заданное число попаданий и количество выполненных итераций:  
  
```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Теперь понятно, что функция дала сбой на 101-м вызове. Если теперь задать точку останова с количеством попаданий 101 и запустить программу снова, она остановится именно на том вызове `CnvtV`, который и привел к сбою.  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Задание точек останова](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
