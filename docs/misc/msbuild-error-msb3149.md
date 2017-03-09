---
title: "Ошибка MSBuild MSB3149 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3149
**MSB3149: ресурсы для построения начального загрузчика недоступны.**  
  
 Эта ошибка появляется, когда не удается найти файлы ресурсов загрузчика \(setup.xml\), соответствующие какому\-либо языку и региональным параметрам.  
  
### Чтобы исправить эту ошибку  
  
-   Откройте **Панель управления**, выберите **Установка и удаление программ** и восстановите пакет Visual Studio SDK или скопируйте файлы в соответствующий каталог \(\<путь\_установки\_SDK\>\\bootstrapper\\engine\\\<язык\>\\setup.xml\).  
  
## См. также  
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)