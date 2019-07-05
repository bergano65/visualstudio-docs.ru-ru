---
title: Решение (. Файл SLN)
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b0e0b09b12dca964958d5d7b35c6b0d83906fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322612"
---
# <a name="solution-sln-file"></a>Файл решения (SLN)

Это решение представляет собой структуру для организации проектов в Visual Studio. Решение хранит сведения о состоянии для проектов в двух файлах:

- SLN-файл (текстовый, общий)

- файл SUO (решение двоичный, пользовательские параметры)

Дополнительные сведения о SUO-файлы, см. в разделе [пользовательских параметров решения (. SUO-) файл](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Если в результате, на которую ссылается SLN-файл загружается VSPackage, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> для чтения в SLN-файл.

SLN-файл содержит сведения, основанные на тексте, которые в среде используется для поиска и загрузки параметров имя значение для материализованных данных и пакеты VSPackage, он ссылается на проект. Когда пользователь открывает решение, среда выполняет циклический переход по `preSolution`, `Project`, и `postSolution` сведения в SLN-файл для загрузки решения, проекты в решении, и любой хранимой информации, к которым решение.

Файл каждый проект содержит дополнительные сведения, полученные с помощью среды для заполнения иерархии с помощью элементов этого проекта. Сохраняемость данных иерархии контролируются проекта. Данные не хранятся обычно в SLN-файл, несмотря на то, что намеренно можно написать о проектах в SLN-файл, если вы решили сделать это. Дополнительные сведения о постоянном хранении см. в разделе [сохранение проекта](../../extensibility/internals/project-persistence.md) и [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Заголовок файла

Заголовок SLN-файл выглядит следующим образом:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Определения

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Стандартный заголовок, который определяет версию формата файла.

`# Visual Studio 15`\
Основной номер версии (последней) сохраненной этот файл решения Visual Studio. Эта информация определяет номер версии в значок решения.

`VisualStudioVersion = 15.0.26730.15`\
Полную версию Visual Studio, который (наиболее недавно) сохранен файл решения. Если файл решения сохранен в более новой версии Visual Studio с той же основной версией, это значение не обновляется таким образом, чтобы уменьшить число обновлений файлов решения.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, можно открыть этот файл решения.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Определения

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Стандартный заголовок, который определяет версию формата файла.

`# Visual Studio Version 16`\
Основной номер версии (последней) сохраненной этот файл решения Visual Studio. Эта информация определяет номер версии в значок решения.

`VisualStudioVersion = 16.0.28701.123`\
Полную версию Visual Studio, который (наиболее недавно) сохранен файл решения. Если файл решения сохранен в более новой версии Visual Studio с той же основной версией, это значение не обновляется таким образом, чтобы уменьшить степень изменения в файле.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, можно открыть этот файл решения.

::: moniker-end

## <a name="file-body"></a>Текст файла

Тело SLN-файл состоит из нескольких разделов с меткой `GlobalSection`, следующим образом:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Чтобы загрузить решение, среде выполняет следующую последовательность задач:

1. Среде считывает общий раздел SLN-файла и обрабатывает все разделы, помеченные `preSolution`. В этом примере файла есть одним из таких операторов:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Когда среде считывает `GlobalSection('name')` тег, он сопоставляет имя с VSPackage с помощью реестра. Имя ключа должна существовать в разделе реестра [HKLM\\< корневой каталог приложения идентификатор реестра\>\SolutionPersistence\AggregateGUIDs]. Параметры по умолчанию для ключей, используется идентификатор GUID пакета (REG_SZ) написал записи пакета VSPackage.

2. Среде загружает VSPackage, вызовы `QueryInterface` в VSPackage для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> интерфейс, а также вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> метод с данными в разделе, поэтому данные можно сохранить пакет VSPackage. Среде этот процесс повторяется для каждого `preSolution` раздел.

3. Среде выполняет итерацию в блоках сохраняемости проекта. В этом случае имеется один проект.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Эта инструкция содержит уникальный идентификатор GUID проекта и идентификатор GUID типа проекта. Эта информация используется в среде, чтобы найти файл проекта или файлов, принадлежащих к решению и VSPackage необходимые для каждого проекта. Идентификатор GUID, переданный для проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> загрузить определенный пакет VSPackage, связанные с проектом, затем проект загружен по VSPackage. В этом случае пакет VSPackage, который загружается для этого проекта — Visual Basic.

   Каждый проект можно сохранить проект уникальный идентификатор экземпляра, таким образом, чтобы он был доступен при необходимости, другие проекты в решении. В идеале Если решение и проекты находятся в системе управления версиями, путь к проекту, должны быть относительно пути к решению. При первой загрузке решения, файлы проекта не может быть на компьютере пользователя. Когда файл проекта, хранящиеся на сервере по отношению к файлу решения, это относительно простой для файла проекта найти и скопировать на компьютере пользователя. А затем копирует и загружает остальные файлы, необходимые для проекта.

4. Среды, исходя из информации, содержащейся в разделе проекта SLN-файл, загружает каждый файл проекта. Сам проект отвечает за заполнение иерархии проекта и загрузки всех вложенных проектов.

5. После обработки всех разделов SLN-файла решение отображается в обозревателе решений и готов для изменения пользователем.

Если не удается загрузить, любой пакет VSPackage, который реализует проект в решении <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> метод вызывается и получает возможность отменить изменения, его может сделать во время загрузки каждого проекта в решении. В случае возникновения ошибки синтаксического анализа столько информации, максимально сохраняется с файлами решения и среде отображает диалоговое окно предупреждение о повреждении решения.

При сохранении или закрытии решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> метод вызывается и передается в иерархию, чтобы увидеть, были ли внесены изменения в решение, которые должны быть введены в SLN-файл. Значение null, переданный для `QuerySaveSolutionProps` в <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, указывает что информация сохраняется для решения. Если значение не равно null, сохраненной информации — для конкретного проекта, определяется указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс.

При наличии сведений для сохранения, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс вызывается с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> метод. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Метод вызывается средой, чтобы получить пары «имя значение» из `IPropertyBag` интерфейса и записывать данные в SLN-файл.

`SaveSolutionProps` и `WriteSolutionProps` объекты называются рекурсивно средой, чтобы получить сведения, которые будут сохраняться с `IPropertyBag` интерфейс, пока все изменения были введены в SLN-файл. Таким образом можно гарантировать, что данные будут сохранены с помощью решения и доступных следующий раз при открытии решения.

Чтобы увидеть, если у него есть действий, которые необходимо сохранить в SLN-файл перечисляется каждого загруженного пакета VSPackage. Это только во время загрузки, который получат разделы реестра. Среды было известно обо всех загруженных пакетов, так как они находятся в памяти во время сохранения решения.

Только в SLN-файл содержит записи в `preSolution` и `postSolution` разделы. Существуют аналогичные ни один из разделов в SUO-файл так, как решение использует эту информацию для загружаться неправильно. SUO-файл содержит пользовательские параметры, такие как частных заметок, которые не предназначены для общих или поместить в систему управления версиями.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Файл параметров пользователя решения (SUO-файл)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Решения](../../extensibility/internals/solutions-overview.md)