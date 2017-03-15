---
title: "Предупреждение о соответствии спецификации CLS CLS02409 | Microsoft Docs"
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
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии спецификации CLS CLS02409
Методы, которые реализуют получение и задание значения, должны быть отмечены в метаданных атрибутом SpecialName  
  
 Методы, которые реализуют получение и задание значения свойства, не помечены в метаданных атрибутом **specialname**.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении функции \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS02409:  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 Чтобы устранить это предупреждение, добавьте ключевое слово **specialname**.  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```