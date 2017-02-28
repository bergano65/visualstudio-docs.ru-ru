---
title: "Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 22c46117f929447dc9a85b940bdaac911b35a7d8
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe
Можно использовать MSBuild.exe для создания конкретных целевых объектов определенных проектов в решении.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении  
  
1.  В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.  
  
2.  Укажите целевой объект после параметра **/t** в формате *имя_проекта*:*имя_целевого_объекта*.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
