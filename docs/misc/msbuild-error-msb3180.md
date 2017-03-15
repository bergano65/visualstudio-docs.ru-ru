---
title: "Ошибка MSBuild MSB3180 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3180
**MSB3180: компонент COM "\<сборка\>" определен как в "\<файл\>", так и в "\<файл\>", clsid\/tlbid\="\<сборка\>".**  
  
 Эта ошибка появляется в процессе создания манифеста приложения, когда обнаружены повторяющиеся ссылки на COM\-объекты \(на классы или библиотеки типов\) либо в ссылках на файлы, либо в зависимых манифестах.  
  
 Например, эта ошибка может появиться при добавлении ссылки на COM\-объект во внешнем манифесте и ссылки на тот же COM\-объект во внутреннем манифесте.  
  
### Чтобы исправить эту ошибку  
  
-   Удалите одну из повторяющихся ссылок на COM\-объект.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)