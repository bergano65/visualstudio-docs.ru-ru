---
title: "Предупреждение компилятора (уровень 2) CS0728 | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 2) CS0728
Возможно, используется недопустимое назначение для локальной переменной "переменная", которая является аргументом оператора using или lock.  В исходном значении локального объекта произойдет вызов Dispose или разблокирование.  
  
 Существует несколько сценариев, где блоки `using` или `lock` приведут к временной утечке ресурсов. Ниже приведен один пример.  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 В этом случае исходное значение, например null, переменной `thisType` будет удалено, когда блок `using` закончит выполнение, но объект `thisType`, созданный в этом блоке, не будет удален, несмотря на то, что он будет в конечном итоге удален сборщиком мусора.  
  
 Чтоб устранить эту ошибку, используйте следующую форму:  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 В данном случае вновь выделенный объект `thisType` будет удален.  
  
## Пример  
 Следующий код приводит к возникновению предупреждения CS0728.  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```