---
title: "Ошибка MSBuild MSB3148 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoOutputPath"
helpviewer_keywords: 
  - "MSB3148"
ms.assetid: 389b335f-5760-4dcc-9146-c52d6d7ac81f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3148
**MSB3148: выходной путь не указан в параметрах построения.**  
  
 Эта ошибка появляется, когда указан нулевой или недопустимый выходной путь; например, если в файле проекта указано `OutputPath=""`.  По умолчанию выходной путь имеет значение `CurrentDirectory`.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что свойство `OutputPath` не осталось пустым или что оно не включено в файл проекта.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)