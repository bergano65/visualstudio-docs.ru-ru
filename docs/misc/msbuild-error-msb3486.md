---
title: "Ошибка MSBuild MSB3486 | Microsoft Docs"
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
  - "MSBuild.SignFile.CertificateError"
helpviewer_keywords: 
  - "MSB3486"
ms.assetid: 75d03d8e-3a28-4010-b602-61fe037dec74
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3486
**MSB3486: Не удается получить сертификат из хранилища "\<хранилище сертификатов\>".**  
  
 Эта ошибка генерируется в MSBuild задачей `ResolveKeySource`, если сертификат, соответствующий отпечатку PFX\-файла проекта, не найден в хранилище личных сертификатов.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что отпечаток из PFX\-файла проекта соответствует сертификату в хранилище личных сертификатов.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)