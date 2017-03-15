---
title: "Ошибка компилятора CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0844
Невозможно использовать локальную переменную "имя" до ее объявления. Объявление этой локальной переменной скрыто в поле "имя".  
  
 Идентификатор может иметь только одно значение в конкретном блоке. Локальные переменные с именами, совпадающими с именами полей класса, могут скрывать поле, придавая второе значение идентификатору. Поэтому компилятор выдает ошибку, когда вы ссылаетесь на поле класса в методе, а затем объявляете локальную переменную с тем же именем.  
  
### Исправление ошибки  
  
-   Используйте `this.num` для создания ссылки на поле класса.  
  
-   Присвойте локальной переменной имя, отличное от имени поля класса.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0844:  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```