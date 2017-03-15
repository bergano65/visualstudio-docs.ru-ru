---
title: "Задача AssignCulture | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AssignCulture - задача [MSBuild]"
  - "MSBuild, AssignCulture - задача"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Задача AssignCulture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Данная задача принимает список элементов, которые могут содержать строку действительного идентификатора языка и региональных параметров .NET в виде части имени файла, и позволяет получить элементы с метаданными `Culture`, содержащими соответствующий идентификатор языка и региональных параметров.  Например, имя файла Form1.fr\-fr.resx имеет встроенный идентификатор языка и региональных параметров "fr\-fr", поэтому задача выдает элемент, который имеет такое же имя файла с метаданными `Culture`, имеющими значение `fr-fr`.  Задача также выдает список имен файлов, в котором из имени файла удален язык и региональные параметры.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `AssignCulture`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AssignedFiles`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит список элементов, полученных в параметре `Files`, где к каждому из них добавлена запись метаданных `Culture`.<br /><br /> Если входящий элемент из параметра `Files` уже содержит запись метаданных `Culture`, то используется исходная запись метаданных.<br /><br /> В задаче запись метаданных `Culture` назначается только в том случае, если имя файла содержит действительный идентификатор языка и региональных параметров.  Идентификатор языка и региональных параметров должен находиться в имени файла между двумя последними точками.|  
|`AssignedFilesWithCulture`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит подмножество элементов из параметра `AssignedFiles`, имеющих запись метаданных `Culture`.|  
|`AssignedFilesWithNoCulture`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит подмножество элементов из параметра `AssignedFiles`, для которых отсутствует запись метаданных `Culture`.|  
|`CultureNeutralAssignedFiles`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Содержит тот же список элементов, который может быть получен с помощью параметра `AssignedFiles`, но в нем из имени файла удален язык и региональные параметры.<br /><br /> Эта задача удаляет язык и региональные параметры из имени файла только в том случае, если оно является действительным идентификатором языка и региональных параметров.|  
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задание списка файлов со встроенными именами языка и региональных параметров для назначения языка и региональных параметров.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере выполняется задача `AssignCulture` с коллекцией элементов `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 В следующей таблице описаны значения выходных элементов после выполнения задачи.  Метаданные элемента показаны справа в круглых скобках.  
  
|Коллекция элементов|Содержимое|  
|-------------------------|----------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(без дополнительных метаданных\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(без дополнительных метаданных\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`без дополнительных метаданных\)|  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)