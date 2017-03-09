---
title: "Ошибка MSBuild MSB3186 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoIdentity"
helpviewer_keywords: 
  - "MSB3186"
ms.assetid: 1219fef4-9114-401c-875b-1dc69697fd9f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3186
**MSB3186: Не удается установить удостоверение сборки для созданного манифеста из входных параметров задачи.**  
  
 Эта ошибка возникает, если в процессе построения не удается установить имя сборки для манифеста приложения или манифеста развертывания.  Имя сборки не указывается в явном виде и в базовом манифесте отсутствует ее удостоверение; удостоверение точки входа также не указывается.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)