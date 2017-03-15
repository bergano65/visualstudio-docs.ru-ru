---
title: "Ошибка MSBuild MSB3184 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3184
**MSB3184: InputManifest недействителен.**  
  
 Эта ошибка выдается при попытке загрузки файла в процессе построения, если ожидается, что файл содержит манифест приложения или манифест развертывания, но оказывается, что он содержит что\-либо другое \(например другой манифест или поврежденные данные\).  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что манифесты в проекте действительны и относятся к соответствующему типу.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)