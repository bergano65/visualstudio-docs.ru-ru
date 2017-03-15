---
title: "Ошибка компилятора CS1731 | Microsoft Docs"
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
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1731
Невозможно преобразовать "выражение" в делегат, поскольку некоторые типы возврата в блоке не могут быть неявно преобразованы в тип возврата делегата  
  
 Эта ошибка возникает, если лямбда\-выражение или анонимный метод имеет тип возврата, который несовместим с типом возврата делегата.  
  
### Исправление ошибки  
  
1.  Измените тип возврата делегата или выражения.  
  
## Пример  
 В следующем коде возникает ошибка CS1731:  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```