---
title: Задача RemoveDuplicates | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73ad829c86305ff4d9a54025467e262d56e24dbc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654520"
---
# <a name="removeduplicates-task"></a>Задача RemoveDuplicates
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Удаляет повторяющиеся элементы из указанной коллекции элементов.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `RemoveDuplicates` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Filtered`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит коллекцию элементов, из которой удалены все повторяющиеся элементы.|  
|`Inputs`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Коллекция элементов, из которой нужно удалить повторяющиеся элементы.|  
  
## <a name="remarks"></a>Примечания  
 Эта задача не учитывает регистр, а также не сравнивает метаданные элементов при определении повторяющихся элементов.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В этом примере показано использование задачи `RemoveDuplicates` для удаления повторяющихся элементов из коллекции элементов `MyItems`. После завершения задачи коллекция элементов `FilteredItems` содержит один элемент.  
  
```  
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
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
