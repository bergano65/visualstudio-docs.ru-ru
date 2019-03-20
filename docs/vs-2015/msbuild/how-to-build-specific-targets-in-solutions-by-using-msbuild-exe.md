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
ms.openlocfilehash: 85c8f3dcb9364c2837cd4d10f163de3795821ce7
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194234"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Можно использовать MSBuild.exe для создания конкретных целевых объектов определенных проектов в решении.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении  
  
1.  В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.  
  
2.  Укажите целевой объект после параметра **/t** в формате *имя_проекта*:*имя_целевого_объекта*.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
