---
title: "Предупреждение компилятора (уровень&#160;1) CS1570 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень&#160;1) CS1570
XML\-комментарий для "конструкция" содержит некорректный XML — "причина"  
  
 Если используется параметр [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option), все комментарии в исходном коде должны быть в формате XML. Любая ошибка разметки XML вызывает предупреждение CS1570. Пример:  
  
-   При передаче строки в атрибут **cref**, например в теге [\<exception\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md), строка должны быть заключена в двойные кавычки.  
  
-   При использовании тега, например [\<seealso\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md), который не имеет закрывающего тега, необходимо поставить косую черту перед закрывающей угловой скобкой.  
  
-   Если в тексте описания необходимо использовать символ "больше" или "меньше", следует представить эти символы как **&gt;** или **&lt;**.  
  
-   Атрибут file или path в теге [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) отсутствует или имеет неправильный формат.  
  
 Следующий пример приводит к возникновению предупреждения CS1570:  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```