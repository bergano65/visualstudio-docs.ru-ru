---
title: "Предупреждение компилятора (уровень 2) CS0280 | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0280
"тип" не реализует шаблон "имя шаблона". "имя метода" имеет неправильную сигнатуру.  
  
 Два оператора C\#, **foreach** и **using**, используют предварительно определенные шаблоны collection и resource соответственно. Это предупреждение возникает, если компилятор не может соотнести какой\-либо из этих операторов с его шаблоном из\-за неправильной сигнатуры метода. Например, для шаблона collection требуется наличие метода <xref:System.Collections.IEnumerator.MoveNext%2A>, который не имеет параметров и возвращает `boolean`. Ваш код может содержать метод <xref:System.Collections.IEnumerator.MoveNext%2A>, который имеет параметр или может возвращать объект.  
  
 Другой пример — шаблон resource и `using`. Для шаблона resource требуется метод <xref:System.IDisposable.Dispose%2A>; если вы определили свойство с тем же именем, вы получите это предупреждение.  
  
 Чтобы устранить это предупреждение, убедитесь, что сигнатуры метода в типе совпадают с сигнатурами соответствующих методов в шаблоне, а также убедитесь, что у вас нет свойств с тем же именем, что и у метода, требуемого шаблоном.  
  
## Пример  
 В следующем примере возникает ошибка CS0280.  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```