---
title: Смешанный код и отсутствующие данные в окне стека вызовов
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32fe52b31daa384718eae629d3051bade93959d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808159"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Смешанный код и отсутствующие данные в окне стека вызовов
Из-за различий между стеками вызовов в управляемом и машинном коде отладчик не всегда может отображать полный стек вызовов для кода смешанного типа. Если машинный код вызывает управляемый код, можно заметить следующие несоответствия в окне **Стек вызовов**:

- Фрейм машинного кода, расположенный непосредственно над управляемым кодом, может отсутствовать в окне **Стек вызовов**. Дополнительные сведения см. в разделе [Практическое руководство. выйти из пошагового выполнения управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов](how-to-use-the-call-stack-window.md).

- В приложениях со смешанным кодом, запущенных вне отладчика, в окне **Стек вызовов** могут отображаться только ссылки на управляемый код, и не будет отображаться ни один из стековых фреймов машинного кода.

  Оба случая встречаются достаточно редко. В большинстве случаев вызова управляемого кода из машинного кода стек вызовов отображается правильно.

## <a name="see-also"></a>См. также
- [Практическое руководство. использование окна "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md)