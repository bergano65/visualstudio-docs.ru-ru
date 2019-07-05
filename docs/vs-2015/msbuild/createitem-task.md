---
title: Задача CreateItem | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 758491a068fe2c2c7318717f5481b41839c49a3f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419765"
---
# <a name="createitem-task"></a>Задача CreateItem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Заполняет коллекцию элементов входными элементами. Это позволяет копировать элементы из одного списка в другой.  
  
> [!NOTE]
> Эта задача является устаревшей. Начиная с .NET Framework 3.5, группы элементов могут размещать внутри элемента [Target](../msbuild/target-element-msbuild.md). Дополнительные сведения см. в разделе [Элементы](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Атрибуты  
 В следующей таблице приводятся параметры задачи `CreateItem` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalMetadata`|Необязательный параметр массива `String`.<br /><br /> Указывает дополнительные метаданные для присоединения к выходным элементам.  Имена и значения метаданных для элемента можно указать с помощью следующего синтаксиса:<br /><br /> *Имя_метаданных* `=` *Значение_метаданных*<br /><br /> Пары имен и значений для метаданных следует разделять точкой с запятой. Если имя или значение содержит точку с запятой или другие специальные символы, их необходимо экранировать. Дополнительные сведения см. в разделе [Как Пропуск специальных знаков в MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает элементы, исключаемые из коллекции выходных элементов. Спецификации в этом параметре могут содержать подстановочные знаки. Дополнительные сведения см. в статьях [Элементы](../msbuild/msbuild-items.md) и [Практическое руководство. Исключить файлы из сборки](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает элементы, включаемые в коллекцию выходных элементов. Спецификации в этом параметре могут содержать подстановочные знаки.|  
|`PreserveExistingMetadata`|Необязательный параметр `Boolean` .<br /><br /> Если он имеет значение `True`, дополнительные метаданные применяются только в том случае, когда они еще не существуют.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода из коллекции элементов `MySourceItems` создается новая коллекция элементов с именем `MySourceItemsWithMetadata`. Задача `CreateItem` заполняет новую коллекцию элементов элементами из элемента `MySourceItems`. Затем она добавляет в каждый элемент новой коллекции дополнительную запись метаданных с именем `MyMetadata` и значением `Hello`.  
  
 После выполнения этой задачи в коллекции элементов `MySourceItemsWithMetadata` содержатся элементы `file1.resx` и `file2.resx`, и для обоих указаны записи метаданных `MyMetadata`. Коллекция элементов `MySourceItems` остается без изменений.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 Следующая таблица описывает значение выходного элемента после выполнения этой задачи. Метаданные элемента представлены в скобках после соответствующего элемента.  
  
|Коллекция элементов|Описание|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
