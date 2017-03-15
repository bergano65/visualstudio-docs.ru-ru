---
title: "Ошибка MSBuild MSB3481 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertNotInStore"
helpviewer_keywords: 
  - "MSB3481"
ms.assetid: 55f99775-3bd5-4e1b-b184-c6405d75e8ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3481
**MSB3481: сертификат подписи не найден.  Убедитесь, что он находится в хранилище личных сертификатов текущего пользователя.**  
  
 Эта ошибка появляется, если в хранилище личных сертификатов не удалось найти сертификат для подписи.  Эта ошибка подобна ошибке [Ошибка MSBuild MSB3486](../misc/msbuild-error-msb3486.md), которая означает, что сертификат был найден, но не соответствует.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что в хранилище личных сертификатов имеется действительный сертификат, соответствующий PFX\-файлу проекта.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)