---
title: "Тип делегата &quot;&lt;имя_делегата&gt;&quot; события &quot;&lt;имя_события&gt;&quot; не является CLS-совместимым | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип делегата &quot;&lt;имя_делегата&gt;&quot; события &quot;&lt;имя_события&gt;&quot; не является CLS-совместимым
Инструкция [Оператор Event](/dotnet/visual-basic/language-reference/statements/event-statement) использует делегат для указания его сигнатуры, но инструкция [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement) помечена как `<CLSCompliant(False)>` или не помечена вообще.  
  
 Когда вы применяете атрибут <xref:System.CLSCompliantAttribute> к программному элементу, вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать на соответствие или несоответствие требованиям. Для этого параметра нет значения по умолчанию, и вы должны предоставить его.  
  
 Если вы не примените <xref:System.CLSCompliantAttribute> к элементу, он считается не соответствующим требованиям.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40050  
  
### Исправление ошибки  
  
-   Если необходима CLS\-совместимость и имеется контроль над определением делегата, примените атрибут <xref:System.CLSCompliantAttribute> к его объявлению, чтобы пометить его как `<CLSCompliant(True)>`.  
  
-   Если вы не можете управлять определением делегата или пометить его как совместимый, удалите <xref:System.CLSCompliantAttribute> из инструкции `Event` или пометьте его как `<CLSCompliant(False)>`.  
  
## См. также  
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)