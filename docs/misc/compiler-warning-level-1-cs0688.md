---
title: "Предупреждение компилятора (уровень&#160;1) CS0688 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS0688
Метод "метод1" содержит запрос компоновки, но переопределяет или реализует метод "метод2", который не имеет запрос компоновки. Может возникнуть нарушение защиты.  
  
 Запрос компоновки, установленный в методе производного класса, можно легко обойти, вызвав метод базового класса. Чтобы закрыть эту брешь в системе безопасности, метод базового класса также должен использовать запрос компоновки. Дополнительные сведения см. в разделе [Demand и LinkDemand](http://msdn.microsoft.com/ru-ru/1ab877f2-70f4-4e0d-8116-943999dfe8f5).  
  
## Пример  
 В следующем примере возникает ошибка CS0688. Чтобы устранить это предупреждение без изменения базового класса, удалите атрибут безопасности из переопределяющего метода. Это не решит проблему безопасности.  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```