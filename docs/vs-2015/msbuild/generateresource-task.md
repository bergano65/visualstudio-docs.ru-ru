---
title: Задача GenerateResource | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: caa267aa44a72d180195a30b41fa7a2c03033bdf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668409"
---
# <a name="generateresource-task"></a>Задача GenerateResource
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Преобразовывает файлы формата TXT и RESX (файлы ресурсов на основе XML) и двоичные RESOURCES-файлы среды CLR, которые могут быть внедрены в двоичный исполняемый файл среды выполнения или скомпилированы во вспомогательные сборки. Обычно эта задача используется для преобразования файлов формата TXT и RESX в RESOURCES-файлы. Задача `GenerateResource` функционально аналогична [resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `GenerateResource` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalInputs`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит дополнительные входные данные для проверки зависимости, выполняемой этой задачей. Например, файлы проекта и целей построения, как правило, должны быть входными данными, чтобы в случае их обновления все ресурсы создались заново.|  
|`EnvironmentVariables`|Необязательный параметр `String[]` .<br /><br /> Указывает массив пар "имя — значение" переменных среды, которые нужно передать в порожденный файл resgen.exe, дополняя (или выборочно переопределяя) обычный блок среды.|  
|`ExcludedInputPaths`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет массив элементов, указывающих пути, из которых отслеживаемые входные данные будут игнорироваться во время проверки наличия обновлений.|  
|`ExecuteAsTool`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, из соответствующей внепроцессной требуемой версии .NET Framework запустятся программы Tlbimp.exe и Aximp.exe для создания необходимых сборок-оболочек. Этот параметр разрешает настройку для различных версий `ResolveComReferences`.|  
|`FilesWritten`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит имена всех файлов, записанных на диск. Включает файл кэша (при его наличии). Этот параметр полезен для реализаций метода Clean.|  
|`MinimalRebuildFromTracking`|Необязательный параметр `Boolean` .<br /><br /> Получает или задает параметр, указывающий, будет ли использоваться отслеживаемая добавочная сборка. Если задано значение `true`, включится добавочная сборка. В противном случае произойдет принудительное выполнение повторной сборки.|  
|`NeverLockTypeAssemblies`|Необязательный параметр `Boolean` .<br /><br /> Указывает имя созданных файлов, например RESOURCES-файлов. Если имя не указано, используется имя соответствующего входного файла, а создаваемый RESOURCES-файл помещается в каталог, содержащий входной файл.|  
|`OutputResources`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает имя созданных файлов, например RESOURCES-файлов. Если имя не указано, используется имя соответствующего входного файла, а создаваемый RESOURCES-файл помещается в каталог, содержащий входной файл.|  
|`PublicClass`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, создает класс ресурса со строгой типизацией как открытый класс.|  
|`References`|Необязательный параметр `String[]` .<br /><br /> Ссылки для загрузки типов в RESX-файлы. Элементы данных RESX-файла могут содержать тип .NET. Этот параметр должен быть разрешен при считывании RESX-файла. Как правило, он разрешается с использованием стандартных правил загрузки типов. Если предоставить сборки в `References`, они будут иметь приоритет.<br /><br /> Для строго типизированных ресурсов этот параметр не требуется.|  
|`SdkToolsPath`|Необязательный параметр `String` .<br /><br /> Указывает путь к средствам пакета SDK, например resgen.exe.|  
|`Sources`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает элементы, которые нужно преобразовать. Элементы, передаваемые этому параметру, должны содержать одно из следующих расширений файлов:<br /><br /> -   `.txt`: указывает расширение текстового файла, который нужно преобразовать. Текстовые файлы могут содержать только строковые ресурсы.<br />-   `.resx`: указывает расширение файла ресурсов на основе XML, который нужно преобразовать.<br />-   `.restext`: Задает тот же формат, что и txt. Это уникальное расширение полезно в том случае, если требуется отделить исходные файлы, содержащие ресурсы, от других исходных файлов в процессе сборки.<br />-   `.resources`: указывает расширение для файла ресурсов, который нужно преобразовать.|  
|`StateFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает путь к необязательному файлу кэша, используемому для ускорения проверки зависимости ссылок во входных RESX-файлах.|  
|`StronglyTypedClassName`|Необязательный параметр `String` .<br /><br /> Указывает имя класса для строго типизированного класса ресурсов. Если этот параметр не указан, используется базовое имя файла ресурсов.|  
|`StronglyTypedFilename`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает имя файла исходного кода. Если этот параметр не указан, используется имя класса в качестве базового имени файла с расширением, зависящим от языка. Например, `MyClass.cs`.|  
|`StronglyTypedLanguage`|Необязательный параметр `String` .<br /><br /> Указывает язык, используемый во время создания источника класса для строго типизированного ресурса. Этот параметр должен полностью совпадать с одним из языков, применяемых CodeDomProvider. Пример: `VB` или `C#`.<br /><br /> Во время передачи значения этому параметру указывается задача по созданию ресурсов со строгой типизацией.|  
|`StronglyTypedManifestPrefix`|Необязательный параметр `String` .<br /><br /> Указывает пространство имен ресурса или префикс манифеста для использования в создаваемом источнике класса для строго типизированного ресурса.|  
|`StronglyTypedNamespace`|Необязательный параметр `String` .<br /><br /> Указывает пространство имен, используемое в создаваемом источнике класса для строго типизированного ресурса. Если этот параметр не указан, все строго типизированные ресурсы находятся в глобальном пространстве имен.|  
|`TLogReadFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`, доступный только для чтения.<br /><br /> Получает массив элементов, представляющих журналы отслеживания чтения.|  
|`TLogWriteFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`, доступный только для чтения.<br /><br /> Получает массив элементов, представляющих журналы отслеживания записи.|  
|`ToolArchitecture`|(Необязательно [String]<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) параметра.<br /><br /> Используется, чтобы определить, нужно ли использовать Tracker.exe для создания ResGen.exe.<br /><br /> Должна обеспечиваться возможность синтаксического анализа до элемента перечисления <xref:Microsoft.Build.Utilities.ExecutableType>. Если задано значение `String.Empty`, используется эвристика для определения архитектуры по умолчанию. Для члена перечисления Microsoft.Build.Utilities.ExecutableType следует задать синтаксический анализ.|  
|`TrackerFrameworkPath`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> .<br /><br /> Задает путь к соответствующему расположению .NET Framework, содержащему FileTracker.dll.<br /><br /> Если значение задано, пользователь отвечает за то, чтобы разрядность передаваемого файла FileTracker.dll соответствовала разрядности файла ResGen.exe, который планируется использовать. Если значение не задано, задача определяет соответствующее расположение на основе текущей версии .NET Framework.|  
|`TrackerLogDirectory`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> .<br /><br /> Задает промежуточный каталог, в котором будут размещены журналы отслеживания для выполнения этой задачи.|  
|`TrackerSdkPath`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> .<br /><br /> Задает путь к соответствующему расположению Windows SDK, содержащему Tracker.exe.<br /><br /> Если значение задано, пользователь отвечает за то, чтобы разрядность передаваемого файла Tracker.exe соответствовала разрядности файла ResGen.exe, который планируется использовать. Если значение не задано, задача определяет соответствующее расположение на основе текущей версии Windows SDK.|  
|`TrackFileAccess`|Необязательно () [логическое]<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) параметра.<br /><br /> Если задано значение true, используется каталог входного файла для разрешения относительных путей к файлам.|  
|`UseSourcePath`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, задается каталог входного файла, который должен использоваться для разрешения относительных путей к файлам.|  
  
## <a name="remarks"></a>Примечания  
 Так как RESX-файлы могут содержать ссылки на другие файлы ресурсов, недостаточно просто сравнивать метки времени файлов с расширением RESX и RESOURCE, чтобы узнать, обновлены ли выходные данные. Вместо этого задача `GenerateResource` следует ссылкам RESX-файлов и проверяет метки времени связанных файлов. Это значит, что атрибуты `Inputs` и `Outputs` не следует использовать в целевом объекте, содержащем задачу `GenerateResource`, так как это может вызвать пропуск при запуске.  
  
 Помимо перечисленных выше параметров эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension> , который в свою очередь наследует от класса <xref:Microsoft.Build.Utilities.Task> . Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 При использовании MSBuild 4.0 для проектов .NET 3.5 в ресурсах x86 может произойти ошибка сборки. Чтобы избежать этой проблемы, можно создать целевой объект, например сборку AnyCPU.  
  
## <a name="example"></a>Пример  
 В следующем примере используется задача `GenerateResource` для создания файлов ресурсов, определенных коллекцией элементов `Resx`.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 Задача `GenerateResource` использует метаданные \<LogicalName> элемента \<EmbeddedResource> для именования ресурса, внедренного в сборку.  
  
 Предположим, что сборка называется myAssembly, а в следующем коде создается внедренный ресурс с именем someQualifier.someResource.resources:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Без метаданных \<LogicalName> ресурс будет называться myAssembly.myResource.resources.  Этот пример применяется только к процессу сборки Visual Basic и Visual C#.  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
