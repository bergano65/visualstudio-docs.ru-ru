---
title: 'Как: применение изменений в режиме приостановки выполнения с помощью изменить и продолжить | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f031598e0c8f290907e759bcfceac85c1b063f5f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Практическое руководство. Применение изменений в режиме приостановки выполнения с помощью режима "Изменить и продолжить"
Можно использовать "Изменить и продолжить" для изменения кода в режиме приостановки и продолжения затем работы без остановки и перезапуска приложения.  
  
Ограничения на с помощью "Изменить и продолжить" во время отладки. в разделе [поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Изменение кода в режиме приостановки  
  
1.  Войдите в режим приостановки, выполнив одно из следующих действий:  
  
    -   Установите точку останова в коде, а затем выберите **начать отладку** из **отладки** меню и ожидания приложение попадет на точке останова.  
  
         - или -  
  
    -   Начните отладку, а затем выберите **прервать все** из **отладки** меню.  
  
         - или -  
  
    -   При возникновении исключения выберите **Разрешить изменение** на**помощник по исключениям**.  
  
2.  Внесите нужные изменения требуемой и поддерживаемый код.  
  
     Дополнительные сведения см. в разделе [поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  При попытке недопустимого режимом "Изменить и продолжить" изменения кода, изменения будут подчеркнуты фиолетовой волнистой линией и соответствующая пометка появится в списке задач. Если не отменить недопустимые изменения кода, возможности продолжить выполнение кода не будет.  
  
3.  На **отладки** меню, нажмите кнопку **Продолжить** для возобновления выполнения.  
  
     Код теперь выполняется с учетом примененных к проекту изменений.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Изменить и продолжить (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)