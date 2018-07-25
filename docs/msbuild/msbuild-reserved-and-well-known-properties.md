---
title: Зарезервированные и стандартные свойства MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72b4fb0d11c1ed100b6ebd124da909e245baa1db
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078918"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства MSBuild
В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предусмотрен набор предопределенных свойств для сохранения информации о файле проекта и двоичных файлах [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Значения этих свойств вычисляются так же, как и значения других свойств [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Например, для использования свойства `MSBuildProjectFile` необходимо ввести `$(MSBuildProjectFile)`  
  
 Для определения зарезервированных и известных свойств в MSBuild используются значения, приведенные в следующей таблице. Зарезервированные свойства переопределить нельзя, тогда как известные свойства можно переопределить с помощью свойств с идентичными именами (свойства среды, глобальные свойства или свойства, определенные в файле проекта).
  
## <a name="reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства  
 В следующей таблице приведены предопределенные свойства, предусмотренные в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Свойство.|Зарезервированное или стандартное|Описание:|
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Зарезервированное|Абсолютный путь к папке, где находятся используемые в данный момент двоичные файлы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] (например, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber*). Этим свойством удобно пользоваться в случае, когда требуется сослаться на файлы в каталоге [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildExtensionsPath`|Стандартное|Введено в .NET Framework 4: разницы между значениями по умолчанию `MSBuildExtensionsPath` и `MSBuildExtensionsPath32` нет. Переменной среды `MSBUILDLEGACYEXTENSIONSPATH` можно присвоить значение, отличное от null, чтобы включить поведение, соответствующее значению по умолчанию `MSBuildExtensionsPath` в предыдущих версиях.<br /><br /> В .NET Framework 3.5 и более ранних версиях значение по умолчанию `MSBuildExtensionsPath` указывает на путь к вложенной папке MSBuild в папке *\Program Files\\* или *\Program Files (x86)*, в зависимости от разрядности текущего процесса. Например, для 32-разрядного процесса на 64-разрядном компьютере это свойство указывает папку на *\Program Files (x86)*. Для 64-разрядного процесса на 64-разрядном компьютере это свойство указывает на папку *\Program Files*.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.<br /><br /> Это расположение хорошо подходит для хранения пользовательских файлов целей. Например, файлы целей можно установить в папку *\Program Files\MSBuild\MyFiles\Northwind.targets*, а затем импортировать в файлы проекта с помощью следующего XML-кода:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|  
|`MSBuildExtensionsPath32`|Стандартное|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в папке *\Program Files\* или *\Program Files (x86)*. Этот путь всегда указывает на папку *\Program Files* на 32-разрядном компьютере и на папку *\Program Files (x86)* на 64-разрядном компьютере. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath64`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
`MSBuildExtensionsPath64`|Стандартное|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в папке *\Program Files*. На 64-разрядном компьютере этот путь всегда указывает на папку *\Program Files*. На 32-разрядном компьютере этот путь будет пустым. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath32`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildLastTaskResult`|Зарезервированное|Значение `true`, если предыдущая задача завершилась без ошибок (даже если были предупреждения), или значение `false`, если в предыдущей задаче были ошибки. Обычно, если в задаче возникает ошибка, эта ошибка — последнее, что происходит в проекте. Следовательно, это свойство никогда не принимает значение `false`, кроме как в следующих сценариях:<br /><br /> — Когда для атрибута `ContinueOnError` [элемента Task (MSBuild)](../msbuild/task-element-msbuild.md) задано значение `WarnAndContinue` (или `true`) или `ErrorAndContinue`.<br /><br /> — Когда `Target` имеет [элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) как дочерний элемент.|  
|`MSBuildNodeCount`|Зарезервированное|Максимальное количество параллельных процессов, используемых при сборке. Это значение, заданное для параметра **/maxcpucount** в командной строке. Если параметр **/maxcpucount** указан без задания значения, `MSBuildNodeCount` определяет количество процессоров в компьютере. Дополнительные сведения см. в разделах [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md) и [Параллельное построение нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|  
|`MSBuildProgramFiles32`|Зарезервированное|Расположение 32-разрядной папки программы; например, *C:\Program Files (x86)*.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildProjectDefaultTargets`|Зарезервированное|Полный список целей, указанных в атрибуте `DefaultTargets` элемента `Project`. Например, для следующего элемента `Project` свойство `MSBuildDefaultTargets` будет иметь значение `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|  
|`MSBuildProjectDirectory`|Зарезервированное|Абсолютный путь к каталогу, где располагается файл проекта, например *C:\MyCompany\MyProduct*.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildProjectDirectoryNoRoot`|Зарезервированное|Значение свойства `MSBuildProjectDirectory`, за исключением корневого диска.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildProjectExtension`|Зарезервированное|Расширение имени файла проекта, включая точку, например *.proj*.|  
|`MSBuildProjectFile`|Зарезервированное|Полное имя файла проекта, включая расширение, например *MyApp.proj*.|  
|`MSBuildProjectFullPath`|Зарезервированное|Абсолютный путь к файлу проекта и его полное имя, включая расширение, например *C:\MyCompany\MyProduct\MyApp.proj*.|  
|`MSBuildProjectName`|Зарезервированное|Имя файла проекта без расширения, например *MyApp*.|  
|`MSBuildRuntimeType`|Зарезервированное|Тип текущей среды выполнения. Представлено в MSBuild 15. Значение может быть не определено (до MSBuild 15), `Full` (указывает на то, что MSBuild выполняется на платформе .NET для ПК), `Core` (указывает на то, что MSBuild выполняется на платформе .NET Core) или `Mono` (указывает на то, что MSBuild выполняется на платформе на Mono).|  
|`MSBuildStartupDirectory`|Зарезервированное|Абсолютный путь к каталогу, из которого вызывается [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. С помощью этого свойства можно собирать все, что находится ниже конкретной точки в дереве проекта, без создания файлов *\<dirs>.proj* в каждом каталоге. Вместо этого у вас будет только один проект — например, *c:\traversal.proj*, как показано ниже:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Чтобы выполнить сборку в любой точке дерева, введите следующее:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|  
|`MSBuildThisFile`|Зарезервированное|Часть `MSBuildThisFileFullPath`, представляющая собой имя и расширение файла.|  
|`MSBuildThisFileDirectory`|Зарезервированное|Часть `MSBuildThisFileFullPath`, представляющая собой каталог.<br /><br /> Включите в путь завершающую обратную косую черту.|  
|`MSBuildThisFileDirectoryNoRoot`|Зарезервированное|Часть `MSBuildThisFileFullPath`, представляющая собой каталог, за исключением корневого диска.<br /><br /> Включите в путь завершающую обратную косую черту.|  
|`MSBuildThisFileExtension`|Зарезервированное|Часть `MSBuildThisFileFullPath`, представляющая собой расширение имени файла.|  
|`MSBuildThisFileFullPath`|Зарезервированное|Абсолютный путь файла проекта или файла целей, содержащего запущенную цель.<br /><br /> Совет. В файле целей можно указать относительный путь, являющийся относительным для файла целей и не являющийся относительным для файла исходного проекта.|  
|`MSBuildThisFileName`|Зарезервированное|Часть `MSBuildThisFileFullPath`, представляющая собой имя файла без расширения.|  
|`MSBuildToolsPath`|Зарезервированное|Путь установки версии [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], связанной со значением `MSBuildToolsVersion`.<br /><br /> Не включайте в путь завершающую обратную косую черту.<br /><br /> Это свойство нельзя переопределить.|  
|`MSBuildToolsVersion`|Зарезервированное|Версия набора инструментов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], используемая для сборки проекта.<br /><br /> Примечание. Набор инструментов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] состоит из задач, целей и средств, используемых для сборки приложения. Средства включают компиляторы *csc.exe* и *vbc.exe*. Дополнительные сведения см. в разделах [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) и [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).|  

## <a name="names-that-conflict-with-msbuild-elements"></a>Имена, которые конфликтуют с элементами MSBuild

Помимо указанных выше, имена, соответствующие элементам языка MSBuild, не могут использоваться для определяемых пользователем свойств, элементов и метаданных элементов:

* VisualStudioProject
* целевого объекта
* PropertyGroup
* Вывод
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Нажмите кнопку
* When
* Otherwise

## <a name="see-also"></a>См. также  
[Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)

[Свойства MSBuild](../msbuild/msbuild-properties.md)
