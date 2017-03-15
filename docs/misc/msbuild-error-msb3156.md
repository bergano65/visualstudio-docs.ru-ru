---
title: "Ошибка MSBuild MSB3156 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.ProductValidation"
helpviewer_keywords: 
  - "MSB3156"
ms.assetid: 98b1bd42-9efe-44a2-8a43-476edc03590d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3156
**MSB3156: Ошибка проверки Xml для элемента "\<пакет\>", расположенного в "\<папка\>".**  
  
 Это предупреждение появляется, если манифест \(а именно product.xml\) не проходит проверку XML.  Конкретные проблемы описаны в последующем сообщении об ошибке \([Ошибка MSBuild MSB3159](/visual-cpp/misc/msbuild-error-msb3159) или [Ошибка MSBuild MSB3160](../misc/msbuild-error-msb3160.md)\).  
  
### Чтобы исправить эту ошибку  
  
-   Устраните проблемы проверки манифеста, указанные в последующих сообщениях об ошибках.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)   
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)