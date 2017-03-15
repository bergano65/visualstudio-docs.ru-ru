---
title: "Делегаты не могут реализовывать методы интерфейсов | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Делегаты не могут реализовывать методы интерфейсов
Делегат — это ссылочный тип, указывающий на общую процедуру или экземпляр процедуры для объекта. Так как процедуру, на которую он указывает, можно изменить путем назначения, оператор `Delegate` не поддерживает предложения `Handles` и `Implements`.  
  
 **Идентификатор ошибки:** BC30018  
  
### Исправление ошибки  
  
-   Удалите предложение `Implements` из оператора `Delegate`.  
  
## См. также  
 [НЕ В СБОРКЕ. Делегаты и оператор AddressOf](http://msdn.microsoft.com/ru-ru/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Оператор Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Оператор Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)