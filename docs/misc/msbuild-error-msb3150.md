---
title: "Ошибка MSBuild MSB3150 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3150
**MSB3150: недоступны строковые ресурсы для сборки начального загрузчика с региональными параметрами "{0}".**  
  
 Эта ошибка появляется, если setup.xml обнаружен, но не содержит узла строк.  Вероятно, файл XML был поврежден.  
  
### Чтобы исправить эту ошибку  
  
-   Откройте **Панель управления**, выберите **Установка и удаление программ** и восстановите пакет Visual Studio SDK или скопируйте файлы в соответствующий каталог \(\<путь\_установки\_SDK\>\\bootstrapper\\engine\\\<язык\>\\setup.xml\).