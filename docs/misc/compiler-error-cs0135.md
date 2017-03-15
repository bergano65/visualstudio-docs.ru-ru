---
title: "Ошибка компилятора CS0135 | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0135
"объявление1" противоречит объявлению "объявление2"  
  
 Компилятор не позволяет скрывать имена, что обычно приводит к логическим ошибкам в коде.  
  
## Пример  
 В следующем примере возникает ошибка CS0135:  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 Из [Спецификация языка C\#](/dotnet/csharp/language-reference/language-specification), раздел 7.5.2.1:  
  
 Для каждого вхождения данного идентификатора в качестве простого имени в выражении или деклараторе в пространстве объявлений локальной переменной \(§3.3\), непосредственно включающем это вхождение, каждое следующее вхождение того же идентификатора в качестве простого имени в выражении или деклараторе должно ссылаться на ту же сущность. Это правило позволяет гарантировать, что внутри определенного блока, блока switch, операторов for, foreach и using или анонимной функции имя всегда имеет одинаковое значение.