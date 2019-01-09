---
title: Эффективное использование памяти при сборке больших проектов | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 958c4c41aea3a147415d799db52c7295234d9488
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858348"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов
Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Ранее старые версии проектов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] оставались в памяти. В версии 3.5 старые версии проектов удаляются, но результаты сборки сохраняются в кэше, чтобы их можно было получить в дальнейшем.  
  
 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.  
  
### <a name="see-also"></a>См. также  
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)