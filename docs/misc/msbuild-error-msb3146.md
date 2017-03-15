---
title: "Ошибка MSBuild MSB3146 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
helpviewer_keywords: 
  - "MSB3146"
ms.assetid: 717fd649-3024-427d-a068-cff8034ffc0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3146
**MSB3146: элемент "\<пакет\>" требуется для "\<пакет\>", но не был включен.**  
  
 Эта ошибка появляется, когда один пакет загрузчика зависит от другого, но для установки выбран только зависимый пакет.  Например, пакет Б зависит от пакета А, но устанавливается только пакет Б.  
  
### Чтобы исправить эту ошибку  
  
-   Включите требуемый пакет.