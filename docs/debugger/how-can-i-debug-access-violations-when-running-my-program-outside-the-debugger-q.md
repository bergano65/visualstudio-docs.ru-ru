---
title: Отладка нарушений доступа при выполнении приложения вне Visual Studio
titleSuffix: ''
description: Использование JIT-отладчика для отладки нарушений доступа, которые происходят за пределами среды Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 49d1fb2b24488692031c647139aa1f1076f0dd6f
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398488"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?

## <a name="problem-description"></a>Описание проблемы
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?

## <a name="solution"></a>Решение
 Активируйте параметр [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md) и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в диалоговом окне **Нарушение доступа** можно нажать **Отмена** и запустить отладчик.

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)