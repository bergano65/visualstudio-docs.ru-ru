---
title: "Эффективное использование памяти при сборке больших проектов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e9484e0b8771ad665f1891298ff2f6a8a1d0005e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов
Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Более старые версии проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], оставшиеся в памяти или в проектах версии 3.5, были удалены, однако результаты сборки остались в кэше для последующего извлечения.  
  
 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.  
  
## <a name="see-also"></a>См. также  
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)