---
title: Как определить конкретный вызов функции, приведший к сбою, если таких вызовов было порядка ста? | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fba5032860e21bbd323b8e49d5f32ab9b6f90540
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688133"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Как определить конкретный вызов функции, приведший к сбою, если таких вызовов было порядка ста?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Описание проблемы  
 Программа дает сбой при вызове некой функции `CnvtV`. Программа, вероятно, вызывает эту функцию перед сбоем пару сотен раз. Если поставить точку останова на `CnvtV`, программа останавливается на каждом вызове этой функции, а этого не требуется. Непонятно, что приводит к сбойному вызову, поэтому поставить условную точку останова невозможно. Что можно сделать?  
  
## <a name="solution"></a>Решение  
 Можно установить точку останова на функции с полем **Количество обращений**, равном недостижимо большому значению. В этом случае, так как предполагается, что функция `CnvtV` вызывается пару сотен раз, **Количество обращений** можно задать 1000 или более. Затем запустить программу и подождать сбоя. Когда сбой произойдет, откройте окно точек останова и просмотрите их список. Точка останова в `CnvtV` появилась, следом появилось заданное число попаданий и количество выполненных итераций:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Теперь понятно, что функция дала сбой на 101-м вызове. Если теперь задать точку останова с количеством попаданий 101 и запустить программу снова, она остановится именно на том вызове `CnvtV`, который и привел к сбою.  
  
## <a name="see-also"></a>См. также  
 [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Задание точек останова](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)
