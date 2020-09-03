---
title: Зарезервированные и стандартные свойства MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181076"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] предусмотрен набор предопределенных свойств для сохранения информации о файле проекта и двоичных файлах [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Значения этих свойств вычисляются так же, как и значения других свойств [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Например, для использования свойства `MSBuildProjectFile` необходимо ввести `$(MSBuildProjectFile)`  
  
 Для определения зарезервированных и известных свойств в MSBuild используются значения, приведенные в следующей таблице. Зарезервированные свойства переопределить нельзя, тогда как известные свойства можно переопределить с помощью свойств с идентичными именами (свойства среды, глобальные свойства или свойства, определенные в файле проекта).  
  
## <a name="reserved-and-well-known-properties"></a>Зарезервированные и известные свойства  
 В следующей таблице приведены предопределенные свойства, предусмотренные в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
|Свойство|Описание|Зарезервированное или известное|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Абсолютный путь к папке, в которой находятся [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] используемые в данный момент двоичные файлы (например, К:\виндовс\микрософт.нет\фрамеворк \\ *versionNumber*). Этим свойством удобно пользоваться в случае, когда требуется сослаться на файлы в каталоге [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildExtensionsPath`|Введено в .NET Framework 4: разницы между значениями по умолчанию `MSBuildExtensionsPath` и `MSBuildExtensionsPath32` нет. Переменной среды `MSBUILDLEGACYEXTENSIONSPATH` можно присвоить значение, отличное от null, чтобы включить поведение, соответствующее значению по умолчанию `MSBuildExtensionsPath` в предыдущих версиях.<br /><br /> В .NET Framework 3.5 и более ранних версиях значение по умолчанию `MSBuildExtensionsPath` указывает на путь к вложенной папке MSBuild в папке \Program Files или \Program Files (x86), в зависимости от разрядности текущего процесса. Например, для 32-разрядного процесса на 64-разрядном компьютере это свойство указывает папку на \Program Files (x86). Для 64-разрядного процесса на 64-разрядном компьютере это свойство указывает на папку \Program Files.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.<br /><br /> Это расположение хорошо подходит для хранения пользовательских файлов целей. Например, файлы целей можно установить в папку \Program Files\MSBuild\MyFiles\Northwind.targets, а затем импортировать в файлы проекта с помощью следующего XML-кода:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Известное|  
|`MSBuildExtensionsPath32`|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] в папке \Program Files\ или \Program Files (x86). Этот путь всегда указывает на папку \Program Files на 32-разрядном компьютере и на папку \Program Files (x86) на 64-разрядном компьютере. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath64`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Известное|  
`MSBuildExtensionsPath64`|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] в папке \Program Files. На 64-разрядном компьютере этот путь всегда указывает на папку \Program Files. На 32-разрядном компьютере этот путь будет пустым. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath32`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Известное|  
|`MSBuildLastTaskResult`|Значение `true`, если предыдущая задача завершилась без ошибок (даже если были предупреждения), или значение `false`, если в предыдущей задаче были ошибки. Обычно, если в задаче возникает ошибка, эта ошибка — последнее, что происходит в проекте. Следовательно, это свойство никогда не принимает значение `false`, кроме как в следующих сценариях:<br /><br /> — Если `ContinueOnError` атрибут [элемента Task (MSBuild)](../msbuild/task-element-msbuild.md) имеет значение `WarnAndContinue` (или `true` ) или `ErrorAndContinue` .<br /><br /> — Когда `Target` содержит [элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) в качестве дочернего элемента.|Зарезервированное|  
|`MSBuildNodeCount`|Максимальное количество параллельных процессов, используемых при сборке. Это значение, указанное для **/maxcpucount** в командной строке. Если вы указали **/maxcpucount** без указания значения, то `MSBuildNodeCount` указывает число процессоров в компьютере. Дополнительные сведения см. в разделе [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md) и [Сборка нескольких проектов в параллельном](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)режиме.|Зарезервировано|  
|`MSBuildProgramFiles32`|Расположение 32-разрядной папки программы; например, `C:\Program Files (x86)`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectDefaultTargets`|Полный список целей, указанных в атрибуте `DefaultTargets` элемента `Project`. Например, для следующего элемента `Project` свойство `MSBuildDefaultTargets` будет иметь значение `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Зарезервированное|  
|`MSBuildProjectDirectory`|Абсолютный путь к каталогу, где располагается файл проекта, например `C:\MyCompany\MyProduct`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectDirectoryNoRoot`|Значение свойства `MSBuildProjectDirectory`, за исключением корневого диска.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectExtension`|Расширение имени файла проекта, включая точку, например ".proj".|Зарезервировано|  
|`MSBuildProjectFile`|Полное имя файла проекта, включая расширение, например "MyApp.proj".|Зарезервированное|  
|`MSBuildProjectFullPath`|Абсолютный путь к файлу проекта и его полное имя, включая расширение, например "C:\MyCompany\MyProduct\MyApp.proj".|Зарезервировано|  
|`MSBuildProjectName`|Имя файла проекта без расширения, например "MyApp".|Зарезервировано|  
|`MSBuildStartupDirectory`|Абсолютный путь к каталогу, из которого вызывается [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. С помощью этого свойства можно собирать все, что находится ниже конкретной точки в дереве проекта, без создания файлов dirs.proj в каждом каталоге. Вместо этого у вас будет только один проект, — например, c:\traversal.proj, как показано ниже:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Чтобы выполнить сборку в любой точке дерева, введите следующее:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFile`|Часть `MSBuildThisFileFullPath`, представляющая собой имя и расширение файла.|Зарезервированное|  
|`MSBuildThisFileDirectory`|Часть `MSBuildThisFileFullPath`, представляющая собой каталог.<br /><br /> Включите в путь завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFileDirectoryNoRoot`|Часть `MSBuildThisFileFullPath`, представляющая собой каталог, за исключением корневого диска.<br /><br /> Включите в путь завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFileExtension`|Часть `MSBuildThisFileFullPath`, представляющая собой расширение имени файла.|Зарезервированное|  
|`MSBuildThisFileFullPath`|Абсолютный путь файла проекта или файла целей, содержащего запущенную цель.<br /><br /> Совет. В файле целей можно указать относительный путь, являющийся относительным для файла целей и не являющийся относительным для файла исходного проекта.|Зарезервированное|  
|`MSBuildThisFileName`|Часть `MSBuildThisFileFullPath`, представляющая собой имя файла без расширения.|Зарезервированное|  
|`MSBuildToolsPath`|Путь установки версии [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], связанной со значением `MSBuildToolsVersion`.<br /><br /> Не включайте в путь завершающую обратную косую черту.<br /><br /> Это свойство нельзя переопределить.|Зарезервированное|  
|`MSBuildToolsVersion`|Версия набора инструментов [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], используемая для сборки проекта.<br /><br /> Примечание. Набор инструментов [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] состоит из задач, целей и средств, используемых для сборки приложения. Средства включают компиляторы csc.exe и vbc.exe. Дополнительные сведения см. в статьях [набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Стандартные и пользовательские конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).|Зарезервированное|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по MSBuild](../msbuild/msbuild-reference.md) [Свойства MSBuild](msbuild-properties1.md)
