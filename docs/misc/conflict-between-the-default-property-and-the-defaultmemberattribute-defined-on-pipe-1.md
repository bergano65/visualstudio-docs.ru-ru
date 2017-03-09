---
title: "Свойство по умолчанию конфликтует с DefaultMemberAttribute определенным в &quot;|1&quot; | Microsoft Docs"
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
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство по умолчанию конфликтует с DefaultMemberAttribute определенным в &quot;|1&quot;
Класс, структура или интерфейс объявляет свойство по умолчанию с ключевым словом [Default](/dotnet/visual-basic/language-reference/modifiers/default), но также применяет атрибут <xref:System.Reflection.DefaultMemberAttribute> для назначения другого члена в качестве члена по умолчанию.  
  
 Тип может иметь не более одного члена по умолчанию. При объявлении свойства по умолчанию Visual Basic автоматически применяет атрибут <xref:System.Reflection.DefaultMemberAttribute> к классу, структуре или интерфейсу, назначающему это свойство.  
  
 **Идентификатор ошибки:** BC32304  
  
### Исправление ошибки  
  
1.  Решите, какой член должен быть членом по умолчанию для класса, структуры или интерфейса.  
  
2.  Удалите конфликтующее объявление \(ключевое слово `Default` или <xref:System.Reflection.DefaultMemberAttribute>\).  
  
## См. также  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)   
 [НЕ В СБОРКЕ. свойства по умолчанию](http://msdn.microsoft.com/ru-ru/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)