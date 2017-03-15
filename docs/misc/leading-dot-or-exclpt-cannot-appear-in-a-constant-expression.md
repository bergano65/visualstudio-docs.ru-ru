---
title: "Константное выражение не может начинаться с символов &quot;.&quot; или &quot;!&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Константное выражение не может начинаться с символов &quot;.&quot; или &quot;!&quot;.
Для доступа к членам \(.\) и доступа к членам словаря \(\!\) требуется выражение, задающее элемент, содержащий член, в большинстве случаев, включая константные выражения. Следующее объявление является неправильным.  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **Идентификатор ошибки:** BC30995  
  
### Исправление ошибки  
  
-   Укажите экземпляр, содержащий элемент, к которому требуется получить доступ.  
  
## См. также  
 [Инициализаторы объектов: именованные и анонимные типы](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Практическое руководство. Объявление экземпляра анонимного типа \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Оператор Const](/dotnet/visual-basic/language-reference/statements/const-statement)