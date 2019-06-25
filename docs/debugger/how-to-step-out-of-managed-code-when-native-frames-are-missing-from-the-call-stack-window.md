---
title: Шаг с выходом C# код, когда фрагменты машинного кода не в стеке вызовов
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 15169fb1cdbba554ee2066f3123ded8c60f7408f
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263364"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Практическое руководство. выход из пошагового выполнения управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов

Если код имеет машинные фреймы, которых нет в окне **Стек вызовов**, шаг с выходом из управляемого кода может привести к непредсказуемым результатам. Чтобы обойти это ограничение, можно вместо команды **Шаг с выходом** использовать точку останова.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Выполнение шага с выходом из управляемого кода, когда фрагменты присущего данному объекту кода не отображаются в окне "Стек вызовов"

1. В присущем данному объекту коде задайте позиционную точку останова после вызова управляемого кода.

2. В меню **Отладка** выберите команду **Продолжить**.

     Когда управляемый вызов завершится, выполнение будет остановлено в точке останова в присущем данному объекту коде.

## <a name="see-also"></a>См. также

- [Практическое руководство. использование окна "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md)