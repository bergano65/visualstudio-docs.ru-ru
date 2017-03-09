---
title: "Ошибка MSBuild MSB3161 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CircularDependency"
helpviewer_keywords: 
  - "MSB3161"
ms.assetid: 2871d071-7c3a-4103-8b14-6ee56564a7f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3161
**MSB3161: обнаружена циклическая зависимость между следующими пакетами: "\<пакет\>"**  
  
 Это предупреждение выдается при наличии циклической зависимости в графе зависимостей пакета загрузчика \(например: A→B→C→A\).  В таких случаях загрузчику не удается определить, какой пакет устанавливать первым.  
  
### Чтобы исправить эту ошибку  
  
-   Устраните циклическую зависимость: либо измените зависимости, описанные в файлах пакета загрузчика, либо не устанавливайте один из независимых пакетов.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)   
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)