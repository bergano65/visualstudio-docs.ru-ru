---
title: "Ошибка компилятора CS0434 | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0434
Пространство имен "ИмяПространстваИмен1" в пространстве имен "ИмяПространстваИмен2" конфликтует с типом "ИмяТипа1" в пространстве имен "ИмяПространстваИмен3"  
  
 Эта ошибка возникает, когда импортированный тип и импортированное вложенное пространство имен имеют одно и то же полное имя. При ссылке на это имя компилятор не может их различить. Если вы можете изменить импортированный исходный код, то эту ошибку можно устранить, изменив имя типа или пространства имен, чтобы оба имени были уникальными в пределах сборки.  
  
 Приведенный ниже код вызывает ошибку CS0434.  
  
## Пример  
 Этот код создает первую копию типа с идентичным полным именем.  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## Пример  
 Этот код создает вторую копию типа с идентичным полным именем.  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## Пример  
 Этот код ссылается на тип с идентичным полным именем.  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```