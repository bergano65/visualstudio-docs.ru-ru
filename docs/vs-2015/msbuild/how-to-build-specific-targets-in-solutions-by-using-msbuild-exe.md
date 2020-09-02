---
title: Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfef86b8ea82077ba7fe3f753f9835c06c3380a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156660"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно использовать MSBuild.exe для создания конкретных целевых объектов определенных проектов в решении.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении  
  
1. В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.  
  
2. Укажите целевой объект после параметра **/t** в формате *имя_проекта*:*имя_целевого_объекта*.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
