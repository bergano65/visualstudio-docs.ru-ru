---
title: "Ошибка MSBuild MSB3188 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3188
**MSB3188: чтобы пометить сборку "\<сборка\>" как обязательную, она должна иметь надежную подпись.**  
  
 Эта ошибка появляется, когда обязательная сборка не имеет надежной подписи.  Она применяется только к манифестам приложений.  
  
### Чтобы исправить эту ошибку  
  
-   Убедитесь, что все сборки, используемые в проекте, имеют надежную подпись.