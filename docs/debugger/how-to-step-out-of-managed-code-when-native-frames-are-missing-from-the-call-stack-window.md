---
title: 'Как: шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов | Документы Microsoft'
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
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e21d45cd65fc6bc6a66f2f7c698952f0cdd788b9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Практическое руководство. Выход из пошагового выполнения управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов
Если код имеет машинные фреймы, которых нет в **стек вызовов** , шаг с выходом из управляемого кода может привести к непредвиденным результатам. Чтобы избежать этого, можно использовать точку останова, а не **шаг с выходом**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Выполнение шага с выходом из управляемого кода, когда фрагменты присущего данному объекту кода не отображаются в окне "Стек вызовов"  
  
1.  В присущем данному объекту коде задайте позиционную точку останова после вызова управляемого кода.  
  
2.  На **отладки** меню, выберите **Продолжить**.  
  
     Когда управляемый вызов завершится, выполнение будет остановлено в точке останова в присущем данному объекту коде.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md)