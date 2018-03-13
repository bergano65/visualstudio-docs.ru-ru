---
title: "Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4437c8030f66ae24d94a83d796c0d0edf7e59c79
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe
Можно использовать MSBuild.exe для создания конкретных целевых объектов определенных проектов в решении.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении  
  
1.  В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.  
  
2. Укажите целевой объект после параметра `/target:` в формате **`ProjectName`**`:`**`TargetName`**. Если в имени проекта содержатся символы `%`, `$`, `@`, `;`, `.`, `(`, `)` или `'`, замените их на `_` в указанном имени целевого объекта.
  
## <a name="example"></a>Пример  
 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения `NewFolder`.  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>Устранение неполадок

Если вы хотите изучить доступные возможности, воспользуйтесь параметром отладки, предоставляемым MSBuild. Задайте переменную среды `MSBUILDEMITSOLUTION=1` и выполните сборку решения. Будет создан файл MSBuild с именем `<SolutionName>.sln.metaproj` и отображением внутреннего представления решения во время построения. Просмотрите это представление, чтобы определить, какие целевые объекты доступны для сборки.

Не выполняйте сборку с этой заданной переменной среды, пока вам не потребуется этом внутреннее представление. Этот параметр может вызвать проблемы сборки в решении.

## <a name="see-also"></a>См. также  
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
