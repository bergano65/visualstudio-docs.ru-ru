---
title: "Атрибут &quot;NonSerialized&quot; не затронет данный член, поскольку его вмещающий класс не представлен как &quot;Serializable&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;NonSerialized&quot; не затронет данный член, поскольку его вмещающий класс не представлен как &quot;Serializable&quot;
По умолчанию классы и их члены не поддерживают сериализацию. Атрибут <xref:System.NonSerializedAttribute> необходим только в том случае, если член сериализуемого класса не должен быть сериализован.  
  
 **Идентификатор ошибки:** BC30772  
  
### Исправление ошибки  
  
-   Добавьте к классу атрибут <xref:System.SerializableAttribute>.  
  
     —или—  
  
-   Удалите атрибут <xref:System.NonSerializedAttribute> из члена.  
  
## См. также  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)