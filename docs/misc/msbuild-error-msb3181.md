---
title: "Ошибка MSBuild MSB3181 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateTargetPath"
helpviewer_keywords: 
  - "MSB3181"
ms.assetid: 49349fc2-3fa1-470d-a5cb-6ad72b93f408
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3181
**MSB3181: два или более файлов имеют один и тот же конечный путь: "\<путь\>".**  
  
 Это предупреждение появляется во время создания манифеста приложения, когда для нескольких указанных в ссылках сборок или файлов используется один и тот же конечный путь.  Путь включает имя файла, и все эти сборки будут переопределять друг друга во время развертывания.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)