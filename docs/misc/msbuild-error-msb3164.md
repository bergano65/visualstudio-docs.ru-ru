---
title: "Ошибка MSBuild MSB3164 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageHomeSiteMissing"
helpviewer_keywords: 
  - "MSB3164"
ms.assetid: 5a1e31fc-0322-4d4e-8c26-013b1efb82c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3164
**MSB3164: Атрибут "HomeSite" не был предоставлен для пакета "\<пакет\>", поэтому пакет будет опубликован в том же расположении, что и загрузчик.**  
  
 Это предупреждение появляется, когда пользователь собирается использовать атрибут HomeSite, но соответствующая информация HomeSite для указанного пакета недоступна.  
  
### Чтобы исправить эту ошибку  
  
-   Обновите файлы манифеста, включив в них информацию HomeSite.  
  
-   Или не используйте атрибут HomeSite.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)