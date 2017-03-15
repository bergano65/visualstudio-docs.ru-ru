---
title: "Недопустимый модификатор &quot;&lt;модификатор&gt;&quot; в объявлении интерфейса | Microsoft Docs"
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
  - "bc30397"
  - "vbc30397"
helpviewer_keywords: 
  - "BC30397"
ms.assetid: 9143dc87-c396-4ff9-9987-0b460ee32b38
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимый модификатор &quot;&lt;модификатор&gt;&quot; в объявлении интерфейса
Используется модификатор, который не является допустимым в объявлении `Interface`. Единственными допустимыми модификаторами для операторов `Sub`, `Function` и `Property`, объявленных в объявлении `Interface`, являются ключевые слова `Overloads` и `Default`. Другие модификаторы, такие как `Public`, `Private`, `Friend`, `Protected`, `Shared`, `Static`, `Overrides`, `MustOverride` и `Overridable`, недопустимы.  
  
 **Идентификатор ошибки:** BC30397  
  
### Исправление ошибки  
  
-   Удалите модификатор.  
  
## См. также  
 [НЕ В СБОРКЕ. Определение интерфейса](http://msdn.microsoft.com/ru-ru/7840a52c-9c38-42c4-adbc-e2c02e9dc204)