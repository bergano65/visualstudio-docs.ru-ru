---
title: "Ошибка MSBuild MSB3158 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.UsingResourcesCulture"
helpviewer_keywords: 
  - "MSB3158"
ms.assetid: 012278dc-961a-468e-b4aa-291a8569e59b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3158
**MSB3158: Не удается найти ресурсы для региональных параметров \<региональные параметры\>.  Вместо этого используются язык и региональные параметры \<язык и региональные параметры\>.**  
  
 Это предупреждение появляется, когда указанному продукту не удается найти файл манифеста пакета \(package.xml\), в котором используются указанные региональные параметры.  
  
### Чтобы исправить эту ошибку  
  
-   Предоставьте соответствующий файл манифеста пакета.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)