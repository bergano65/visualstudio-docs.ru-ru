---
title: "Ошибка MSBuild MSB3142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CopyError"
helpviewer_keywords: 
  - "MSB3142"
ms.assetid: acca7437-6c72-446c-a6b5-a1c051b6855f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3142
**MSB3142: при копировании "\<файл\>" в "\<папка\>" произошла ошибка: "\<ошибка\>"**  
  
 Эта ошибка появляется при копировании файла setup.bin в выходной каталог построения.  Возможные причины этой ошибки:  
  
-   Нет разрешения на копирование в выходной каталог.  
  
-   Диск заполнен.  
  
 Потенциальные причины те же, что и при появлении ошибки file.copy или directory.createdirectory.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)