---
title: Как отладить нарушения доступа при запуске программы без отладчика? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3e4a79ba90f887f11c3fd9a7bddf318ace35cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?
## <a name="problem-description"></a>Описание проблемы  
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?  
  
## <a name="solution"></a>Решение  
 Задать [непосредственно времени отладки](../debugger/just-in-time-debugging-in-visual-studio.md) параметр и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в **нарушение прав доступа** диалоговое окно, следует щелкнуть **отменить** для запуска отладчика.  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)