---
title: Как выполнить Сборка конкретных целевых объектов в решениях с помощью MSBuild.exe | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53ce05490ac46d7a4f01010e5709364f5d35222d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977257"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Как выполнить Сборка конкретных целевых объектов в решениях с помощью MSBuild.exe
Можно использовать *MSBuild.exe* для создания конкретных целевых объектов определенных проектов в решении.

#### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении

1. В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.

2. Укажите целевой объект после параметра `-target:` в формате \<имя_проекта>:\<имя_целевого_объекта>. Если в имени проекта содержатся символы `%`, `$`, `@`, `;`, `.`, `(`, `)` или `'`, замените их на `_` в указанном имени целевого объекта.

## <a name="example"></a>Пример
 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения *Новая_папка*.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Устранение неполадок

Если вы хотите изучить доступные возможности, воспользуйтесь параметром отладки, предоставляемым MSBuild. Задайте переменную среды `MSBUILDEMITSOLUTION=1` и выполните сборку решения. Будет создан файл MSBuild с именем *\<SolutionName>.sln.metaproj*, который отображает внутреннее представление решения во время построения. Просмотрите это представление, чтобы определить, какие целевые объекты доступны для сборки.

Не выполняйте сборку с этой заданной переменной среды, пока вам не потребуется этом внутреннее представление. Этот параметр может вызвать проблемы сборки в решении.

## <a name="see-also"></a>См. также
- [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
