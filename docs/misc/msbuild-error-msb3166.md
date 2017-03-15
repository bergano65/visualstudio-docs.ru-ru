---
title: "Ошибка MSBuild MSB3166 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageResourceFileNotFound"
  - "vsdeploy.chm:13166"
helpviewer_keywords: 
  - "MSB3166"
ms.assetid: f5dff83a-1e41-4c92-a137-89b7e9f3cd93
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3166
**MSB3166: не удалось найти требуемый файл "\<файл\>" для элемента "\<пакет\>".**  
  
 Эта ошибка появляется, когда отсутствует лицензионное соглашение конечного пользователя или файл внешней проверки.  Убедитесь, что файл существует на диске.  
  
### Чтобы исправить эту ошибку  
  
-   Переустановите пакет Visual Studio SDK.  
  
     \- или \-  
  
-   Скопируйте требуемые файлы в соответствующее расположение.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)