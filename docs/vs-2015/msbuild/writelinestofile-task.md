---
title: Задача WriteLinesToFile | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af63679437e0b128472d084a55f1ef24a93bc4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301851"
---
# <a name="writelinestofile-task"></a>Задача WriteLinesToFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Записывает пути указанных элементов в заданный текстовый файл.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `WriteLinestoFile`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает файл, в который нужно записать элементы.|  
|`Lines`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает элементы, которые нужно записать в файл.|  
|`Overwrite`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, задача перезаписывает существующее содержимое файла.|  
|`Encoding`|Необязательный параметр `String` .<br /><br /> Выбирает кодировку символов, например Юникод.  См. также раздел <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Примечания  
 Если `Overwrite` имеет значение `true`, создается файл, в него записывается содержимое, а затем файл закрывается. Если целевой файл уже существует, он будет переопределен. Если `Overwrite` имеет значение `false`, содержимое добавляется к файлу. Если конечный файл не существует, он создается.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В этом примере задача `WriteLinesToFile` используется для записи путей к элементам из коллекции `MyItems` в файл, указанный в коллекции элементов `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



