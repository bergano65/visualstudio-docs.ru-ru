---
title: "Предупреждение компилятора (уровень 1) CS1684 | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS1684
Не удается найти тип "Имя типа", который, согласно ссылке, должен быть определен в "Пространство имен".  
  
 Эта ошибка может быть вызвана ссылкой в одном пространстве имен на тип, который, как подразумевается, существует в другом пространства имен, но этот тип не существует. Например, mydll.dll говорит, что тип `A` существует в yourdll.dll, но в yourdll.dll такой тип отсутствует. Одной из возможных причин этой ошибки является использование слишком старой версии yourdll.dll, в которой еще не был определен тип `A`.  
  
 В следующем примере возникает ошибка CS1684.  
  
## Пример  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## Пример  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## Пример  
 Теперь мы выполним повторную сборку первой сборки, оставляя определение класса C2 не должен определенным при перекомпиляции.  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## Пример  
 Этот модуль ссылается на второй модуль посредством идентификатора `Ref`. Но второй модуль содержит ссылку на класс `C2`, которого больше не существует после компиляции на предыдущем шаге, и поэтому при компиляции этого модуля возвращается сообщение об ошибке CS1684.  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```