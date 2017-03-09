---
title: "Ошибка MSBuild MSB3154 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
helpviewer_keywords: 
  - "MSB3154"
ms.assetid: 513b70fa-15f5-4137-bdbc-5974607fb75a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3154
**MSB3154: не удалось найти строковые ресурсы для элемента "\<пакет\>".**  
  
 Эта ошибка появляется, когда указанный пакет не содержит сведений, относящихся к конкретному языку и региональным параметрам.  Файл package.xml не существует или не содержит атрибута `Culture`.  
  
### Чтобы исправить эту ошибку  
  
-   Предоставьте допустимый файл package.xml, содержащий правильный тег `Culture`.