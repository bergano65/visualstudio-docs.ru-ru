---
title: 'Практическое: применение изменений в режиме приостановки выполнения с помощью изменить и продолжить | Документация Майкрософт'
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
ms.openlocfilehash: f45b2a64e7602d038a12f436019a8f99e352aa26
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257081"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Практическое: применение изменений в режиме приостановки выполнения с помощью изменить и продолжить (Visual Basic)
Можно использовать "Изменить и продолжить" для изменения кода в режиме приостановки и продолжения затем работы без остановки и перезапуска приложения.  
  
Ограничений по использованию изменить и продолжить во время отладки, см. в разделе [поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Изменение кода в режиме приостановки  
  
1.  Войдите в режим приостановки, выполнив одно из следующих действий:  
  
    -   Установите точку останова в коде, а затем выберите **начать отладку** из **Отладка** меню и дождитесь приложение попадет на точке останова.  
  
         - или -  
  
    -   Начать отладку, а затем выберите **прервать все** из **Отладка** меню.  
  
         - или -  
  
    -   При возникновении исключения выберите **Разрешить изменение** на **исключениям**.  
  
2.  Внося изменения в требуемые и поддерживаемый код.  
  
     Дополнительные сведения см. в разделе [поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  При попытке недопустимого режимом "Изменить и продолжить" изменения кода, изменения будут подчеркнуты фиолетовой волнистой линией и соответствующая пометка появится в списке задач. Если не отменить недопустимые изменения кода, возможности продолжить выполнение кода не будет.  
  
3.  На **Отладка** меню, щелкните **Продолжить** для возобновления выполнения.  
  
     Код теперь выполняется с учетом примененных к проекту изменений.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые изменения кода (C# и Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Изменить и продолжить (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)