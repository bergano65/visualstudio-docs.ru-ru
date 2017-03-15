---
title: "Ошибка MSBuild MSB3144 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidInput"
helpviewer_keywords: 
  - "MSB3144"
ms.assetid: 955e0db3-afe2-4c03-8e95-3419878374df
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3144
**MSB3144: предоставлено недостаточно данных для создания начального загрузчика.  Укажите значение по крайней мере для одного из следующих параметров: "ApplicationFile" или "BootstrapperItems".**  
  
 Эта ошибка появляется, если было предоставлено недостаточно данных для создания загрузчика.  В процессе построения создается пустой загрузчик без установщика приложения и пакетов.  
  
### Чтобы исправить эту ошибку  
  
-   Укажите значение хотя бы для одного из следующих параметров: `ApplicationFile` или `BootstrapperItems`.  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)