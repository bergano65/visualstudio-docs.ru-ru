---
title: Файлы TARGETS в MSBuild | Документация Майкрософт
description: Сведения о TARGETS-файлах MSBuild, которые содержат элементы, свойства, целевые объекты и задачи для обычных сценариев.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee685fc3deada1a3ac36082fa916b50986900f81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971249"
---
# <a name="msbuild-targets-files"></a>Файлы TARGETS в MSBuild

MSBuild включает в себя несколько *TARGETS*-файлов, содержащих элементы, свойства, целевые объекты и задачи для обычных сценариев. Эти файлы автоматически импортируются в большинство файлов проекта Visual Studio для упрощения обслуживания и улучшения читаемости.

 Обычно проекты импортируют один или несколько *TARGETS*-файлов для определения своего процесса сборки. Например, проект C#, созданный Visual Studio, будет импортировать *Microsoft.CSharp.targets*, который импортирует *Microsoft.Common.targets*. Сам проект C# будет определять элементы и свойства, относящиеся к данному проекту, а стандартные правила сборки для проекта C# определяются в импортированных *TARGETS*-файлах.

 Значение `$(MSBuildToolsPath)` определяет путь к этим общим *TARGETS*-файлам. Если `ToolsVersion` имеет значение 4.0, файлы находятся в следующем расположении: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Дополнительные сведения о создании собственных целевых объектов см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md). Сведения об использовании элемента `Import` для вставки файла проекта в другой файл проекта см. в разделах [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md) и [Практическое руководство. Использование одного и того же целевого объекта в нескольких файлах проектов](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Общие файлы TARGETS

| Файл *TARGETS* | Описание |
|---------------------------------| - |
| *Microsoft.Common.targets* | Определяет этапы стандартного процесса сборки для проектов Visual Basic и C#.<br /><br /> Импортированы с помощью файлов *Microsoft.CSharp.targets* и *Microsoft.VisualBasic.targets*, которые включают в себя следующий оператор: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Определяет этапы стандартного процесса сборки для проектов Visual C#.<br /><br /> Импортированы с помощью файлов проекта Visual C# (с расширением *CSPROJ*), которые включают в себя следующий оператор: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Определяет этапы стандартного процесса сборки для проектов Visual Basic.<br /><br /> Импортированы с помощью файлов проекта Visual Basic (с расширением *VBPROJ*), которые включают в себя следующий оператор: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* является определяемым пользователем файлом, который содержит настройки для проектов в каталоге. Этот файл автоматически импортируется из *Microsoft.Common.targets*, пока свойству **ImportDirectoryBuildTargets** не будет назначено значение **false**. Дополнительные сведения см. в статье [Настройка сборки](customize-your-build.md).

## <a name="see-also"></a>См. также

- [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
