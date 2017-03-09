---
title: "Ошибка MSBuild MSB3157 | Microsoft Docs"
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
  - "vsdeploy.chm:13157"
  - "MSBuild.GenerateBootstrapper.UsingProductCulture"
helpviewer_keywords: 
  - "MSB3157"
ms.assetid: ccfcbea4-eb9b-42ae-9908-47079ecc84a7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3157
**MSB3157: не удалось найти соответствующие региональные параметры "\<язык\>" для элемента "\<пакет\>".  Вместо этого используются язык и региональные параметры \<язык и региональные параметры\>.**  
  
 Это предупреждение появляется, когда указанному продукту не удается найти файл манифеста пакета \(package.xml\), в котором используются указанные региональные параметры.  
  
### Чтобы исправить эту ошибку  
  
-   Предоставьте соответствующий файл манифеста пакета.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)