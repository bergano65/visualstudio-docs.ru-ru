---
title: Смешанный код и отсутствующие данные в окне стека вызовов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c91b2e49dc94057ab7929380ad1b819cd01731d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563484"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Смешанный код и отсутствующие данные в окне стека вызовов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [смешанный код и отсутствующие данные в окне стека вызовов](https://docs.microsoft.com/visualstudio/debugger/mixed-code-and-missing-information-in-the-call-stack-window).  
  
Из-за различий между стеками вызовов в управляемом и машинном коде отладчик не всегда может отображать полный стек вызовов для кода смешанного типа. Когда машинный код вызывает управляемый код, вы можете заметить следующие несоответствия в **стек вызовов** окна:  
  
-   Возможно, отсутствует фрейм машинного кода, расположенный непосредственно над управляемым кодом **стек вызовов** окна. Дополнительные сведения см. в разделе [как: шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Для смешанных приложений, запущенных вне отладчика **стек вызовов** окно может отображаться только управляемый код и ни один из стековых фреймов машинного кода будет отображаться.  
  
 Оба случая встречаются достаточно редко. В большинстве случаев вызова управляемого кода из машинного кода стек вызовов отображается правильно.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md)





