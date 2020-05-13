---
title: Решение (. Sln) файл
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705332"
---
# <a name="solution-sln-file"></a>Файл решения (.sln)

Решением является структура для организации проектов в Visual Studio. Решение поддерживает информацию о состоянии для проектов в двух файлах:

- файл .sln (текстовый, общий)

- Файл .suo (двоичные варианты решений для конкретных пользователей)

Для получения дополнительной информации о файлах .suo [см. Suo) Файл](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Если ваш VSPackage загружается в результате ссылки в файле .sln, среда призывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> читать в файле .sln.

Файл .sln содержит текстовую информацию, на которой среда использует для поиска и загрузки параметров имено-стоимости для упорных данных, и проект VSPackages, на который он ссылается. Когда пользователь открывает решение, окружающая среда `preSolution` `Project`циклов `postSolution` через , и информация в файле .sln для загрузки решения, проекты в решении, и любой сохраняемый информации, прилагаемые к решению.

Файл каждого проекта содержит дополнительную информацию, считываемую средой для заполнения иерархии элементами этого проекта. Сохранение данных иерархии контролируется проектом. Данные обычно не хранятся в файле .sln, хотя вы можете намеренно записывать информацию о проекте в файл .sln, если вы решите сделать это. Для получения дополнительной информации о настойчивости [см.](../../extensibility/internals/project-persistence.md) [Opening and Saving Project Items](../../extensibility/internals/opening-and-saving-project-items.md)

## <a name="file-header"></a>Заголовок файла

Заголовок файла .sln выглядит следующим образом:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Определения

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Стандартный заголовок, определяющий версию формата файла.

`# Visual Studio 15`\
Основная версия Visual Studio, которая (совсем недавно) сохранила этот файл решения. Эта информация контролирует номер версии в значке решения.

`VisualStudioVersion = 15.0.26730.15`\
Полная версия Visual Studio, которая (совсем недавно) сохранила файл решения. Если файл решения сохраняется более новой версией Visual Studio, которая имеет ту же основную версию, это значение не обновляется, чтобы уменьшить отток в файлах решений.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, которая может открыть этот файл решения.

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
Стандартный заголовок, определяющий версию формата файла.

`# Visual Studio Version 16`\
Основная версия Visual Studio, которая (совсем недавно) сохранила этот файл решения. Эта информация контролирует номер версии в значке решения.

`VisualStudioVersion = 16.0.28701.123`\
Полная версия Visual Studio, которая (совсем недавно) сохранила файл решения. Если файл решения сохраняется более новой версией Visual Studio, которая имеет ту же основную версию, это значение не обновляется, чтобы уменьшить отток в файле.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Минимальная (самая старая) версия Visual Studio, которая может открыть этот файл решения.

::: moniker-end

## <a name="file-body"></a>Тело файла

Тело файла .sln состоит из нескольких `GlobalSection`разделов с пометкой, как это:

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

Для загрузки решения среда выполняет следующую последовательность задач:

1. Окружающая среда читает глобальный раздел файла .sln и обрабатывает все разделы с пометкой. `preSolution` В этом примере файла есть одно такое утверждение:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Когда среда читает `GlobalSection('name')` тег, он отображает имя на VSPackage с помощью реестра. Ключевое имя должно существовать в реестре в соответствии с «HKLM\\<Регистрация идентификатора приложения Корень\>(SolutionPersistence») Агрегированные. Значение ключей по умолчанию — это пакет GUID (REG_SZ) VSPackage, который написал записи.

2. Среда загружает VSPackage, вызывает `QueryInterface` VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> для интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> и вызывает метод с данными в разделе, чтобы VSPackage мог хранить данные. Среда повторяет этот процесс `preSolution` для каждого раздела.

3. Окружающая среда итерирует сятизм проекта через блоки сохранения проекта. В этом случае есть один проект.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Это заявление содержит уникальный проект GUID и тип проекта GUID. Эта информация используется средой для поиска файла проекта или файлов, принадлежащих к решению, и VSPackage, необходимых для каждого проекта. Проект GUID передается <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> для загрузки конкретного VSPackage, связанных с проектом, то проект загружается VSPackage. В этом случае VSPackage, который загружается для этого проекта, является Visual Basic.

   Каждый проект может сохранить уникальный идентификатор экземпляра проекта, чтобы к нему можно было получить доступ по мере необходимости другими проектами в решении. В идеале, если решение и проекты находятся под контролем исходного кода, путь к проекту должен быть относительно пути к решению. При первой загрузке решения файлы проекта не могут быть на машине пользователя. Благодаря хранению файла проекта на сервере по отношению к файлу решения, найти файл проекта относительно просто и скопировать его на компьютер пользователя. Затем он копирует и загружает остальные файлы, необходимые для проекта.

4. На основе информации, содержащейся в разделе проекта файла .sln, среда загружает каждый файл проекта. Затем сам проект отвечает за заполнение иерархии проектов и загрузку любых вложенных проектов.

5. После обработки всех разделов файла .sln решение отображается в Solution Explorer и готово к модификации пользователем.

Если какой-либо VSPackage, который реализует проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> в решении, не загружается, метод вызывается, и каждому другому проекту в решении предоставляется возможность игнорировать изменения, которые он мог бы внести во время загрузки. При обнаружении ошибок в разборе столько информации сохраняется с помощью файлов решений, а среда отображает диалоговую будку, предупреждающую пользователя о повреждении решения.

При сохранении или закрытии <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> решения метод вызывается и передается в иерархию, чтобы увидеть, были ли внесены изменения в решение, которое необходимо ввести в файл .sln. Нулевая величина, передаваемые `QuerySaveSolutionProps` в <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, указывает на то, что информация сохраняется для решения. Если значение не является нулевым, упорная информация предназначена для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> конкретного проекта, определяемого указателем на интерфейс.

Если есть информация, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> которая должна быть сохранена, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> интерфейс вызывается с указателем на метод. Затем <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> метод вызывается средой для извлечения пар `IPropertyBag` имено-ценности из интерфейса и записи информации в файл .sln.

`SaveSolutionProps`и `WriteSolutionProps` объекты повторяются средой для получения информации, которая `IPropertyBag` будет сохранена из интерфейса до тех пор, пока все изменения не будут внесены в файл .sln. Таким образом, вы можете гарантировать, что информация будет сохраняться с решением и доступны в следующий раз решение будет открыт.

Каждый загруженный VSPackage перечисляется, чтобы увидеть, если он имеет что-нибудь сохранить в .sln файл. Запрашиваются только во время загрузки ключи реестра. Среда знает обо всех загруженных пакетах, поскольку они находятся в памяти на момент сохранения решения.

Только файл .sln содержит записи в разделах `preSolution` и `postSolution` разделах. Подобных разделов в файле .suo нет, так как для правильной загрузки этой информации требуется эта информация. Файл .suo содержит пользовательские параметры, такие как частные заметки, которые не предназначены для совместного использования или размещения под контролем исходного кода.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Файл параметров пользователя решения (SUO-файл)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Решения](../../extensibility/internals/solutions-overview.md)
