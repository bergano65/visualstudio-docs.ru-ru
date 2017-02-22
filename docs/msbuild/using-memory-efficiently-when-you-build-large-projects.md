---
title: "Эффективное использование памяти при построении больших проектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "кэширование (MSBuild)"
  - "использование памяти (MSBuild)"
  - "msbuild, эффективное использование памяти при построении деревьев большого размера"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Эффективное использование памяти при построении больших проектов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время построения.  При сокращении объема доступной системной памяти может понизиться производительность системы.  Предыдущие версии проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] сохранялись в памяти или удалялись, как в версии 3.5, но при этом в кэше оставались результаты построения для последующей загрузки.  
  
 В версии 4.0 управление памятью происходит автоматически, проекты сохраняются из\-за необходимого использования таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.  
  
## См. также  
 [Параллельное построение нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)