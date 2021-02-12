---
title: Сборка конкретных целевых объектов в решениях с помощью MSBuild.exe
description: Сведения о том, как использовать командную строку MSBuild.exe для создания конкретных целей определенных проектов в решениях.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ede73e06575a91cf9bdf8115942c27b1ce4e2841
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914474"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Практическое руководство. Построение особых целей в решениях с помощью MSBuild.exe

Можно использовать *MSBuild.exe* для создания конкретных целевых объектов определенных проектов в решении.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Создание конкретного целевого объекта определенного проекта в решении

1. В командной строке введите `MSBuild.exe <SolutionName>.sln`, где `<SolutionName>` соответствует имени файла решения, содержащего целевой объект, который требуется выполнить.

2. Укажите целевой объект после параметра `-target:` в формате \<ProjectName>:\<TargetName>. Если в имени проекта содержатся символы `%`, `$`, `@`, `;`, `.`, `(`, `)` или `'`, замените их на `_` в указанном имени целевого объекта.

## <a name="example"></a>Пример

 В следующем примере выполняется целевой объект `Rebuild` проекта `NotInSlnFolder`, а затем выполняется целевой объект `Clean` проекта `InSolutionFolder`, который находится в папке решения *Новая_папка*.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>Устранение неполадок

Если вы хотите изучить доступные возможности, воспользуйтесь параметром отладки, предоставляемым MSBuild. Задайте переменную среды `MSBUILDEMITSOLUTION=1` и выполните сборку решения. Будет создан файл MSBuild с именем *\<SolutionName>.sln.metaproj*, который отображает внутреннее представление решения во время построения. Просмотрите это представление, чтобы определить, какие целевые объекты доступны для сборки.

Не выполняйте сборку с этой заданной переменной среды, пока вам не потребуется этом внутреннее представление. Этот параметр может вызвать проблемы сборки в решении. Вместо этого обратитесь к [двоичным файлам журнала](obtaining-build-logs-with-msbuild.md#save-a-binary-log).

## <a name="see-also"></a>См. также раздел

- [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
