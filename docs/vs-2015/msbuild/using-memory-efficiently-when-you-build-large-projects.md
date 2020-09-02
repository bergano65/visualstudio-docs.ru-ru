---
title: Эффективное использование памяти при сборке больших проектов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178301"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Более старые версии проектов [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], оставшиеся в памяти или в проектах версии 3.5, были удалены, однако результаты сборки остались в кэше для последующего извлечения.  
  
 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.  
  
## <a name="see-also"></a>См. также:  
 [Параллельное создание нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
