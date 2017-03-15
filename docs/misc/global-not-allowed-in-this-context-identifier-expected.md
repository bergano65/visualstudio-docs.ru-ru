---
title: "Global нельзя использовать в данном контексте; требуется идентификатор | Microsoft Docs"
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
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Global нельзя использовать в данном контексте; требуется идентификатор
Ключевое слово `Global` используется в операторе, в котором оно не допускается.  
  
 Ключевое слово `Global` позволяет получить доступ к пространству имен, определенному вне иерархии пространств имен, в которой компилируется код. При использовании `Global` путь квалификации начинается на самом внешнем уровне пространства имен библиотеки классов .NET Framework. Пример см. в разделе [Global](http://msdn.microsoft.com/ru-ru/18c8ba14-40f6-4978-8096-6a5852324635).  
  
 Некоторые операторы, такие как `Imports` и `Namespace`, не зависят от пространства имен, в котором компилируется ваш код. Они требуют полного пути квалификации, начинающегося с пространства имен корневого уровня, например <xref:System> или <xref:Microsoft.VisualBasic>. В таких операторах ключевое слово `Global` является избыточным и не разрешается.  
  
 **Идентификатор ошибки:** BC36001  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Global` из оператора. Оно не требуется.  
  
## См. также  
 [Global – delete](http://msdn.microsoft.com/ru-ru/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Оператор Imports \(пространство имен .NET и тип\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Оператор Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Ссылки и оператор Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)