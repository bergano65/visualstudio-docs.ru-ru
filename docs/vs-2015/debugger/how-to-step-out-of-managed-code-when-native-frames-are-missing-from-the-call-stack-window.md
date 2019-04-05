---
title: Практическое руководство. Шаг с выходом из управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6cb3b1f0d1c21a7cde53f8b3eecf1cd25c26b394
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990091"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Практическое руководство. выход из пошагового выполнения управляемого кода, когда фрагменты машинного кода не отображаются в окне стека вызовов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если код имеет машинные фреймы, которых нет в окне **Стек вызовов**, шаг с выходом из управляемого кода может привести к непредсказуемым результатам. Чтобы обойти это ограничение, можно вместо команды **Шаг с выходом** использовать точку останова.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Выполнение шага с выходом из управляемого кода, когда фрагменты присущего данному объекту кода не отображаются в окне "Стек вызовов"  
  
1.  В присущем данному объекту коде задайте позиционную точку останова после вызова управляемого кода.  
  
2.  В меню **Отладка** выберите команду **Продолжить**.  
  
     Когда управляемый вызов завершится, выполнение будет остановлено в точке останова в присущем данному объекту коде.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. использование окна "Стек вызовов"](../debugger/how-to-use-the-call-stack-window.md)
