---
title: "Зарезервированные и стандартные свойства MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 29
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 078576d6e1988bf1cefbb09646ea44f61085f5cf
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-reserved-and-well-known-properties"></a>Зарезервированные и стандартные свойства MSBuild
В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предусмотрен набор предопределенных свойств для сохранения информации о файле проекта и двоичных файлах [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Значения этих свойств вычисляются так же, как и значения других свойств [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Например, для использования свойства `MSBuildProjectFile` необходимо ввести `$(MSBuildProjectFile)`  
  
 Для определения зарезервированных и известных свойств в MSBuild используются значения, приведенные в следующей таблице. Зарезервированные свойства переопределить нельзя, тогда как известные свойства можно переопределить с помощью свойств с идентичными именами (свойства среды, глобальные свойства или свойства, определенные в файле проекта).  
  
## <a name="reserved-and-well-known-properties"></a>Зарезервированные и известные свойства  
 В следующей таблице приведены предопределенные свойства, предусмотренные в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Свойство|Описание|Зарезервированное или известное|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Абсолютный путь к папке, где находятся используемые в данный момент двоичные файлы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] (например, C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Этим свойством удобно пользоваться в случае, когда требуется сослаться на файлы в каталоге [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildExtensionsPath`|Введено в .NET Framework 4: разницы между значениями по умолчанию `MSBuildExtensionsPath` и `MSBuildExtensionsPath32` нет. Переменной среды `MSBUILDLEGACYEXTENSIONSPATH` можно присвоить значение, отличное от null, чтобы включить поведение, соответствующее значению по умолчанию `MSBuildExtensionsPath` в предыдущих версиях.<br /><br /> В .NET Framework 3.5 и более ранних версиях значение по умолчанию `MSBuildExtensionsPath` указывает на путь к вложенной папке MSBuild в папке \Program Files или \Program Files (x86), в зависимости от разрядности текущего процесса. Например, для 32-разрядного процесса на 64-разрядном компьютере это свойство указывает папку на \Program Files (x86). Для 64-разрядного процесса на 64-разрядном компьютере это свойство указывает на папку \Program Files.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.<br /><br /> Это расположение хорошо подходит для хранения пользовательских файлов целей. Например, файлы целей можно установить в папку \Program Files\MSBuild\MyFiles\Northwind.targets, а затем импортировать в файлы проекта с помощью следующего XML-кода:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Известное|  
|`MSBuildExtensionsPath32`|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в папке \Program Files\ или \Program Files (x86). Этот путь всегда указывает на папку \Program Files на 32-разрядном компьютере и на папку \Program Files (x86) на 64-разрядном компьютере. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath64`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Известное|  
`MSBuildExtensionsPath64`|Путь к вложенной папке [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в папке \Program Files. На 64-разрядном компьютере этот путь всегда указывает на папку \Program Files. На 32-разрядном компьютере этот путь будет пустым. См. также `MSBuildExtensionsPath` и `MSBuildExtensionsPath32`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Известное|  
|`MSBuildLastTaskResult`|Значение `true`, если предыдущая задача завершилась без ошибок (даже если были предупреждения), или значение `false`, если в предыдущей задаче были ошибки. Обычно, если в задаче возникает ошибка, эта ошибка — последнее, что происходит в проекте. Следовательно, это свойство никогда не принимает значение `false`, кроме как в следующих сценариях:<br /><br /> — Когда для атрибута `ContinueOnError` [элемента Task (MSBuild)](../msbuild/task-element-msbuild.md) задано значение `WarnAndContinue` (или `true`) или `ErrorAndContinue`.<br /><br /> — Когда `Target` имеет [элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) как дочерний элемент.|Зарезервированное|  
|`MSBuildNodeCount`|Максимальное количество параллельных процессов, используемых при сборке. Это значение, заданное для параметра **/maxcpucount** в командной строке. Если параметр **/maxcpucount** указан без задания значения, `MSBuildNodeCount` определяет количество процессоров в компьютере. Дополнительные сведения см. в разделах [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md) и [Параллельное построение нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Зарезервированное|  
|`MSBuildProgramFiles32`|Расположение 32-разрядной папки программы; например, `C:\Program Files (x86)`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectDefaultTargets`|Полный список целей, указанных в атрибуте `DefaultTargets` элемента `Project`. Например, для следующего элемента `Project` свойство `MSBuildDefaultTargets` будет иметь значение `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Зарезервированное|  
|`MSBuildProjectDirectory`|Абсолютный путь к каталогу, где располагается файл проекта, например `C:\MyCompany\MyProduct`.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectDirectoryNoRoot`|Значение свойства `MSBuildProjectDirectory`, за исключением корневого диска.<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildProjectExtension`|Расширение имени файла проекта, включая точку, например ".proj".|Зарезервированное|  
|`MSBuildProjectFile`|Полное имя файла проекта, включая расширение, например "MyApp.proj".|Зарезервированное|  
|`MSBuildProjectFullPath`|Абсолютный путь к файлу проекта и его полное имя, включая расширение, например "C:\MyCompany\MyProduct\MyApp.proj".|Зарезервированное|  
|`MSBuildProjectName`|Имя файла проекта без расширения, например "MyApp".|Зарезервированное|  
|`MSBuildStartupDirectory`|Абсолютный путь к каталогу, из которого вызывается [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. С помощью этого свойства можно собирать все, что находится ниже конкретной точки в дереве проекта, без создания файлов dirs.proj в каждом каталоге. Вместо этого у вас будет только один проект, — например, c:\traversal.proj, как показано ниже:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Чтобы выполнить сборку в любой точке дерева, введите следующее:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Не включайте в это свойство завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFile`|Часть `MSBuildThisFileFullPath`, представляющая собой имя и расширение файла.|Зарезервированное|  
|`MSBuildThisFileDirectory`|Часть `MSBuildThisFileFullPath`, представляющая собой каталог.<br /><br /> Включите в путь завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFileDirectoryNoRoot`|Часть `MSBuildThisFileFullPath`, представляющая собой каталог, за исключением корневого диска.<br /><br /> Включите в путь завершающую обратную косую черту.|Зарезервированное|  
|`MSBuildThisFileExtension`|Часть `MSBuildThisFileFullPath`, представляющая собой расширение имени файла.|Зарезервированное|  
|`MSBuildThisFileFullPath`|Абсолютный путь файла проекта или файла целей, содержащего запущенную цель.<br /><br /> Совет. В файле целей можно указать относительный путь, являющийся относительным для файла целей и не являющийся относительным для файла исходного проекта.|Зарезервированное|  
|`MSBuildThisFileName`|Часть `MSBuildThisFileFullPath`, представляющая собой имя файла без расширения.|Зарезервированное|  
|`MSBuildToolsPath`|Путь установки версии [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], связанной со значением `MSBuildToolsVersion`.<br /><br /> Не включайте в путь завершающую обратную косую черту.<br /><br /> Это свойство нельзя переопределить.|Зарезервированное|  
|`MSBuildToolsVersion`|Версия набора инструментов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], используемая для сборки проекта.<br /><br /> Примечание. Набор инструментов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] состоит из задач, целей и средств, используемых для сборки приложения. Средства включают компиляторы csc.exe и vbc.exe. Дополнительные сведения см. в разделах [Набор инструментов (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) и [Стандартные и настраиваемые конфигурации наборов инструментов](../msbuild/standard-and-custom-toolset-configurations.md).|Зарезервированное|  
  
## <a name="see-also"></a>См. также  
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)
 [Свойства MSBuild](../msbuild/msbuild-properties.md)
