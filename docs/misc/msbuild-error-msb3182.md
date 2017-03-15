---
title: "Ошибка MSBuild MSB3182 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3182
**MSB3182: имя файла "\<файл\>" превышает "\<длина\>" символов.**  
  
 Это предупреждение появляется, когда свойство `TargetPath` имеет слишком длинное значение.  Это применимо и к манифесту приложения, и к манифесту развертывания.  
  
### Чтобы исправить эту ошибку  
  
-   Измените значение свойства `TargetPath`, сделав его короче.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)