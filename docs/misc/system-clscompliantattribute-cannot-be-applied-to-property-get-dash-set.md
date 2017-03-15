---
title: "Атрибут System.CLSCompliantAttribute нельзя применять к операторам Get и Set свойства. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут System.CLSCompliantAttribute нельзя применять к операторам Get и Set свойства.
Определение свойства применяет атрибут <xref:System.CLSCompliantAttribute> к оператору `Get` или `Set` этого свойства.  
  
 Чтобы свойство было совместимо с [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), все свойство должно быть помечено как `<CLSCompliant(True)>`. Необходимо применить атрибут <xref:System.CLSCompliantAttribute> к оператору [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement), но не к оператору `Get` или `Set`.  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить значение.  
  
 Если вы не примените <xref:System.CLSCompliantAttribute> к элементу, он считается несоответствующим требованиям.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40043  
  
### Исправление ошибки  
  
-   Удалите <xref:System.CLSCompliantAttribute> из оператора `Get` или `Set`.  
  
-   Если свойство должно быть CLS\-совместимыми, пометьте оператор `Property` как `<CLSCompliant(True)>`.  
  
## См. также  
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement)