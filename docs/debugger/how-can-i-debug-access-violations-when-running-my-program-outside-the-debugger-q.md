---
title: Отладка нарушений доступа при выполнении приложения вне отладчика
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 88dde869e6e9e1551459ce1171364709baf6403e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350437"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?

## <a name="problem-description"></a>Описание проблемы
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?

## <a name="solution"></a>Решение
 Активируйте параметр [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md) и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в диалоговом окне **Нарушение доступа** можно нажать **Отмена** и запустить отладчик.

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)