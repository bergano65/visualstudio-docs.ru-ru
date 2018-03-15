---
title: "Задача RemoveDuplicates | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ce3271b84d4d6bbb4f7905294d0c9fad678c1b8f
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="removeduplicates-task"></a>Задача RemoveDuplicates
Удаляет повторяющиеся элементы из указанной коллекции элементов.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `RemoveDuplicates` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Filtered`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит коллекцию элементов, из которой удалены все повторяющиеся элементы. При этом порядок входных элементов остается неизменным и сохраняется первый экземпляр каждого повторяющегося элемента.|  
|`Inputs`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Коллекция элементов, из которой нужно удалить повторяющиеся элементы.|  
  
## <a name="remarks"></a>Примечания  
 Эта задача не учитывает регистр, а также не сравнивает метаданные элементов при определении повторяющихся элементов.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В этом примере показано использование задачи `RemoveDuplicates` для удаления повторяющихся элементов из коллекции элементов `MyItems`. После завершения задачи коллекция элементов `FilteredItems` содержит один элемент.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

 В примере ниже видно, что в задаче `RemoveDuplicates` сохраняется порядок входных элементов. По завершении задачи в коллекции элементов `FilteredItems` содержатся элементы MyFile2.cs, MyFile1.cs и MyFile3.cs в указанном порядке.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile2.cs"/>  
        <MyItems Include="MyFile1.cs" />  
        <MyItems Include="MyFile3.cs" />  
        <MyItems Include="myfile1.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
