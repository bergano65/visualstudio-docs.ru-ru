---
title: Поиск вызова, вызвавшего сбой, при многократном вызове функции
description: Сведения о том, как установить точку останова в функции таким образом, что останов происходил только в вызове, для которого функция завершается сбоем.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8937b58277450198d7c0927d93118c492faedfbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883887"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Как определить конкретный вызов функции, приведший к сбою, если таких вызовов было порядка ста?
## <a name="problem-description"></a>Описание проблемы
 Программа дает сбой при вызове некой функции `CnvtV`. Программа, вероятно, вызывает эту функцию перед сбоем пару сотен раз. Если поставить точку останова на `CnvtV`, программа останавливается на каждом вызове этой функции, а этого не требуется. Непонятно, что приводит к сбойному вызову, поэтому поставить условную точку останова невозможно. Что можно сделать?

## <a name="solution"></a>Решение
 Можно установить точку останова на функции с полем **Количество обращений**, равном недостижимо большому значению. В этом случае, так как предполагается, что функция `CnvtV` вызывается пару сотен раз, **Количество обращений** можно задать 1000 или более. Затем запустить программу и подождать сбоя. Когда сбой произойдет, откройте окно точек останова и просмотрите их список. Точка останова в `CnvtV` появилась, следом появилось заданное число попаданий и количество выполненных итераций:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Теперь понятно, что функция дала сбой на 101-м вызове. Если теперь задать точку останова с количеством попаданий 101 и запустить программу снова, она остановится именно на том вызове `CnvtV`, который и привел к сбою.

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Задание точек останова](/previous-versions/ktf38f66(v=vs.100))
- [Отладка машинного кода](../debugger/debugging-native-code.md)