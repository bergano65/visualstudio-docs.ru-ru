---
title: "Ошибка MSBuild MSB3141 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.MissingVerificationInformation"
  - "vsdeploy.chm:13141"
helpviewer_keywords: 
  - "MSB3141"
ms.assetid: f32ce5fd-bb82-4a8b-aebe-61efef89cdc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3141
**MSB3141: атрибут "PublicKey" или "Hash" не указан для файла "\<файл\>" в элементе "\<пакет\>".**  
  
 Эта ошибка появляется при попытке использовать атрибут HomeSite для пакетов загрузчика.  Однако манифест загрузчика не содержит правильной информации для проверки файла \(открытого ключа или хэш\-кода\) во время выполнения.  
  
### Чтобы исправить эту ошибку  
  
-   Загрузите файл пакета, для которого отсутствует информация, и скопируйте его в кэш загрузчика.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)