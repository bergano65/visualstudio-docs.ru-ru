---
title: "Оператор не содержит объявления метода Get или Set | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор не содержит объявления метода Get или Set
Оператору не удается предоставить объявление `Get` или `Set` для процедуры `Property`. Свойство определено в виде блока кода, заключенного в операторы `Property` и `End Property`. Внутри этого блока каждая процедура `Property` представляет собой внутренний блок, заключенный в оператор объявления и оператор End.  
  
 **Идентификатор ошибки:** BC30576  
  
### Исправление ошибки  
  
-   Укажите оператор объявления `Get` или `Set`.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)