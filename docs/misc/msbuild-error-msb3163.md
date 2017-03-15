---
title: "Ошибка MSBuild MSB3163 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3163
**MSB3163: входной параметр построения "ComponentsLocation\=\<расположение\_элементов\>" недопустим.  Значение должно быть одним из следующих: "HomeSite", "Relative" или "Absolute".  Установлено значение по умолчанию "HomeSite".**  
  
 Эта ошибка появляется, когда указано недопустимое значение свойства `ComponentsLocation` \(расположение, из которого устанавливаются необходимые компоненты\).  Свойство `ComponentsLocation` может принимать одно из трех значений: `HomeSite`, `Relative` или `Absolute`.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)