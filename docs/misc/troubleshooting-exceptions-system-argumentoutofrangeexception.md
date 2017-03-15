---
title: "Разрешение вопросов, связанных с исключениями: System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ArgumentOutOfRangeException - класс"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.ArgumentOutOfRangeException
Исключение <xref:System.ArgumentOutOfRangeException> генерируется, когда вызывается метод и хотя бы один из передаваемых ему аргументов не является нулевой ссылкой \(в Visual Basic \- `Nothing`\) и при этом не содержит допустимого значения.  
  
## Полезные советы  
 **Убедитесь, что все аргументы для этого метода имеют допустимые значения, определяемые вызванным методом.**  
 Аргументы, которые не являются пустыми ссылками, должны содержать допустимые значения.  
  
 **Если вы работаете с коллекцией, убедитесь, что индекс меньше, чем размер коллекции.**  
 Значение индекса должно быть в пределах коллекции и не может превышать размер диапазона или быть меньше нуля. Дополнительные сведения см. в разделе [Коллекции](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 **При использовании перегруженных двух\-аргументных методов FindString или FindStringExact класса ComboBox или ListBox, проверьте параметр startIndex**.  
 Это исключение может быть сгенерировано если `startIndex` равно значению индекса последнего элемента связанного списка. Чтобы обойти это, передайте 0 как параметр `startIndex` или используйте одноаргументный метод `FindString` или `FindStringExact`. Дополнительные сведения см. в разделе [CComboBox::FindString](../Topic/CComboBox::FindString.md) или [CListBox::FindString](../Topic/CListBox::FindString.md).  
  
## См. также  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)