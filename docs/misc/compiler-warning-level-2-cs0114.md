---
title: "Предупреждение компилятора (уровень 2) CS0114 | Microsoft Docs"
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
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0114
"функция1" скрывает унаследованный член "функция2". Чтобы текущий метод переопределял реализацию, добавьте ключевое слово override. В противном случае добавьте ключевое слово new.  
  
 Объявление в классе конфликтует с объявлением в базовом классе, поэтому член базового класса будет скрыт.  
  
 Для получения дополнительной информации см. раздел [base](/dotnet/csharp/language-reference/keywords/base).  
  
 Следующий пример приводит к возникновению ошибки CS0114:  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```