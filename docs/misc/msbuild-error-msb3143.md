---
title: "Ошибка MSBuild MSB3143 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.CopyPackageError"
helpviewer_keywords: 
  - "MSB3143"
ms.assetid: b4278c8c-31df-4b4f-9ef9-7b9327e8ee77
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3143
**MSB3143: произошла ошибка при попытке копирования "\<файл\>" элемента "\<пакет\>": "\<ошибка\>"**  
  
 Эта ошибка появляется при копировании пакетов загрузчика в выходной каталог построения.  Возможные причины этой ошибки:  
  
-   Нет разрешения на копирование в выходной каталог построения.  
  
-   Диск заполнен.  
  
 Потенциальные причины те же, что и при появлении ошибки file.copy или directory.createdirectory.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)   
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)