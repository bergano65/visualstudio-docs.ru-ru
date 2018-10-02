---
title: Эффективное использование памяти при сборке больших проектов | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563782"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [с использованием памяти эффективно при вы сборки больших проектов](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects).  
  
  
Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Более старые версии проектов [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], оставшиеся в памяти или в проектах версии 3.5, были удалены, однако результаты сборки остались в кэше для последующего извлечения.  
  
 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.  
  
## <a name="see-also"></a>См. также  
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



