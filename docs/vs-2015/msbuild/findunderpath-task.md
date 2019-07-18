---
title: Задача FindUnderPath | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c679352fb8db81379ab93e800efa9f631773c36
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666615"
---
# <a name="findunderpath-task"></a>Задача FindUnderPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет, какие элементы в указанной коллекции имеют пути в указанной папке или на более низком уровне.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FindUnderPath` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает файлы, пути которых следует сравнивать с путем, заданным в параметре `Path`.|  
|`InPath`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит элементы, найденные по указанному пути.|  
|`OutOfPath`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит элементы, не найденные по указанному пути.|  
|`Path`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает путь к папке для использования в качестве ссылки.|  
|`UpdateToAbsolutePaths`|Необязательный параметр `Boolean` .<br /><br /> Если имеет значение true, пути к выходным элементам изменяются на абсолютные.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В этом примере задача `FindUnderPath` используется для определения наличия в файлах, содержащихся в элементе `MyFiles`, путей ниже указанного в свойстве `SearchPath`. По завершении выполнения задачи элемент `FilesNotFoundInPath` содержит файл `File1.txt`, а элемент `FilesFoundInPath` содержит файл `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
