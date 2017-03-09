---
title: "Ошибка MSBuild MSB3145 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3145
**MSB3145: Входной параметр построения "\<свойство\>\=\<значение\>" не является URL\-адресом веб\-ресурса или UNC\-адресом общего ресурса.**  
  
 Если значение `SupportUrl`, `ComponentsUrl` или `ApplicationUrl` свойства проекта не является допустимым, то возникает ошибка.  Значением должен быть правильный URL\-адрес или путь к UNC\-ресурсу.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)