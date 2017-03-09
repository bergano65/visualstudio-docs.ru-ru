---
title: "Ошибка MSBuild MSB3165 | Microsoft Docs"
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
  - "vsdeploy.chm:13165"
  - "MSBuild.GenerateBootstrapper.DifferingPublicKeys"
helpviewer_keywords: 
  - "MSB3165"
ms.assetid: 2f50462e-947d-4211-b197-e58eddcfd373
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3165
**MSB3165: значение атрибута "\<открытый ключ\>" в "\<пакет\>" не соответствует значению в файле "\<файл\>".**  
  
 Это предупреждение появляется, когда открытый ключ, заданный в файле пакета загрузчика, не соответствует подписи распространяемого пакета на диске или распространяемый пакет не подписан.  В процессе построения будет взято значение открытого ключа из файла на диске, если пакет подписан, или хэш\-код распространяемого пакета на диске, если он не подписан.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)