---
title: "Предупреждение компилятора (уровень 1) CS3014 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS3014
Для "элемент" не требуется атрибут CLSCompliant, так как сборка не имеет атрибута CLSCompliant  
  
 В файле исходного кода, для которого не указано соответствие со спецификацией CLS, конструктор в файле был помечен как CLS\-совместимый. Это не допускается. Чтобы устранить это предупреждение, добавьте в файл атрибут CLS\-совместимости уровня сборки \(в следующем примере раскомментируйте строку, которая содержит атрибут уровня сборки\). Дополнительные сведения о CLS\-совместимости см. в разделах [Написание CLS\-совместимого кода](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3) и [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Пример  
 В следующем примере возникает предупреждение CS3014:  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```