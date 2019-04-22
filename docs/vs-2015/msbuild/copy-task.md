---
title: Задача Copy | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 805a8d6616b4f6c198173ad2a9c9d733ad50de32
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648711"
---
# <a name="copy-task"></a>Задача Copy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Копирование файлов в новое расположение в файловой системе.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `Copy` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`CopiedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит успешно скопированные элементы.|  
|`DestinationFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает список, в который будут скопированы исходные файлы. Предполагается, что этот список будет взаимно-однозначно сопоставляться со списком в параметре `SourceFiles`. То есть первый файл из списка `SourceFiles` будет скопирован с использованием первого пути, заданного в списке `DestinationFiles`, и т. д.|  
|`DestinationFolder`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает каталог, в который требуется скопировать файлы. Это должен быть каталог, а не файл. Если каталог не существует, он создается автоматически.|  
|`OverwriteReadOnlyFiles`|Необязательный параметр `Boolean` .<br /><br /> Перезапись файлов, даже доступных только для чтения.|  
|`Retries`|Необязательный параметр `Int32` .<br /><br /> Задает количество повторений операции копирования в случае неудачи всех предыдущих попыток. По умолчанию установлен нуль.<br /><br /> **Примечание.** Использование повторных попыток может маскировать проблемы синхронизации в процессе сборки.|  
|`RetryDelayMilliseconds`|Необязательный параметр `Int32` .<br /><br /> Определяет задержку между любыми необходимыми попытками. По умолчанию равен аргументу RetryDelayMillisecondsDefault, который передается в конструктор CopyTask.|  
|`SkipUnchangedFiles`|Необязательный параметр `Boolean` .<br /><br /> При значении `true` неизмененные файлы не копируются. В задаче `Copy` неизмененными считаются файлы одного размера с одинаковым временем последнего изменения. **Примечание.** Если этому параметру присвоено значение `true`, то выполнять анализ зависимостей в каталоге, содержащем целевые объекты, не следует, так как эта задача выполняется только в том случае, если время последнего изменения исходных файлов больше, чем у целевых файлов.|  
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает копируемые файлы.|  
|`UseHardlinksIfPossible`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, создает жесткие ссылки для скопированных файлов вместо того, чтобы копировать файлы.|  
  
## <a name="warnings"></a>Предупреждения  
 Регистрируются следующие предупреждения.  
  
-   `Copy.DestinationIsDirectory`  
  
-   `Copy.SourceIsDirectory`  
  
-   `Copy.SourceFileNotFound`  
  
-   `Copy.CreatesDirectory`  
  
-   `Copy.HardLinkComment`  
  
-   `Copy.RetryingAsFileCopy`  
  
-   `Copy.FileComment`  
  
-   `Copy.RemovingReadOnlyAttribute`  
  
## <a name="remarks"></a>Примечания  
 Можно указать либо параметр `DestinationFolder`, либо `DestinationFiles`, но не оба одновременно. В противном случае задача прерывает работу и в журнале регистрируется ошибка.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода выполняется копирование элементов из коллекции `MySourceFiles` в папку c:\MyProject\Destination.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFolder="c:\MyProject\Destination"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется использование рекурсивного копирования. В этом проекте выполняется рекурсивное копирование всех файлов из папки c:\MySourceTree в папку c:\MyDestinationTree с сохранением структуры каталогов.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
