---
title: "Задача WriteLinesToFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteLinesToFile - задача"
  - "WriteLinesToFile - задача [MSBuild]"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача WriteLinesToFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Запись путей к выбранным элементам в указанный текстовый файл.  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `WriteLinestoFile`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задание файла, в который необходимо записать элементы.|  
|`Lines`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задание элементов, которые необходимо записать в файл.|  
|`Overwrite`|Необязательный параметр типа `Boolean`.<br /><br /> Если присвоено значение `true`, задача перезаписывает все содержимое файла.|  
|`Encoding`|Необязательный параметр типа `String`.<br /><br /> Выберите кодировку, например, «Юникод».  См. также раздел <xref:System.Text.Encoding>.|  
  
## Заметки  
 Если `Overwrite` равно `true`, создает новый файл, записывает в него содержимое и затем закрывает файл.  Если целевой файл уже существует, он будет переопределен.  Если `Overwrite` равно `false`, добавляет указанную строку в файл, создавая файл, если он не существует.  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `WriteLinesToFile` используется для записи путей к элементам из коллекции элементов `MyItems` в файл, указанный с помощью коллекции элементов `MyTextFile`.  
  
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
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)