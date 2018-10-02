---
title: Задача ReadLinesFromFile | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0afe1b991f8fb0c4e3a37512f89228cabcde11d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563292"
---
# <a name="readlinesfromfile-task"></a>Задача ReadLinesFromFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача ReadLinesFromFile](https://docs.microsoft.com/visualstudio/msbuild/readlinesfromfile-task).  
  
  
Считывает список элементов из текстового файла.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ReadLinesFromFile` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает файл, который нужно прочитать. Этот файл должен иметь по одному элементу на каждой строке.|  
|`Lines`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит строки, считываемые из файла.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `ReadLinesFromFile` для создания элементов из списка в текстовом файле. Считанные из файла элементы хранятся в коллекции элементов `ItemsFromFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
    </ItemGroup>  
  
    <Target Name="ReadFromFile">  
        <ReadLinesFromFile  
            File="@(MyTextFile)" >  
            <Output  
                TaskParameter="Lines"  
                ItemName="ItemsFromFile"/>  
        </ReadLinesFromFile>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Задачи](../msbuild/msbuild-tasks.md)



