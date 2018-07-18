---
title: Смешанный код и отсутствующие данные в окне стека вызовов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b2733cbf5d9b833ac23ee573e1f39e9c8750224
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480232"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Смешанный код и отсутствующие данные в окне стека вызовов
Из-за различий между стеками вызовов в управляемом и машинном коде отладчик не всегда может отображать полный стек вызовов для кода смешанного типа. Когда машинный код вызывает управляемый код, можно заметить следующие несоответствия в **стек вызовов** окна:  
  
-   Стековый фрейм машинного непосредственно над управляемым кодом может отсутствовать в **стек вызовов** окна. Дополнительные сведения см. в разделе [как: шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Для приложений, запущенных вне отладчика, в смешанном режиме **стек вызовов** могут отображаться только управляемый код, и будет отображаться ни один из стековых фреймов машинного кода.  
  
 Оба случая встречаются достаточно редко. В большинстве случаев вызова управляемого кода из машинного кода стек вызовов отображается правильно.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md)