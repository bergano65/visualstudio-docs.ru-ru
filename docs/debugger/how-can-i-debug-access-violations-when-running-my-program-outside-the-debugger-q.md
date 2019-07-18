---
title: Отладка нарушения прав доступа при запуске приложения вне отладчика
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d42dd206117885a23a6c1c15c712be4dc4cd8fe2
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177674"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?

## <a name="problem-description"></a>Описание проблемы
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?

## <a name="solution"></a>Решение
 Активируйте параметр [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md) и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в диалоговом окне **Нарушение доступа** можно нажать **Отмена** и запустить отладчик.

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)