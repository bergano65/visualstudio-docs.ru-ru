---
title: Задача WriteLinesToFile | Документы Майкрософт
ms.date: 09/20/2018
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 577a87d9faccbb110011eb1fe9bdc6ddb6b3d732
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919373"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile - задача
Записывает пути указанных элементов в заданный текстовый файл.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `WriteLinestoFile` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает файл, в который нужно записать элементы.|  
|`Lines`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает элементы, которые нужно записать в файл.|  
|`Overwrite`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, задача перезаписывает существующее содержимое файла.|  
|`Encoding`|Необязательный параметр `String` .<br /><br /> Выбирает кодировку символов, например Юникод.  См. также раздел <xref:System.Text.Encoding>.|  
|`WriteOnlyWhenDifferent`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, то указанный целевой файл (если он существует) будет считываться первым для сравнения с данными, которые записала бы задача. Если они совпадают, то файл не записывается на диск, а метка времени сохраняется.|  

## <a name="remarks"></a>Примечания  
 Если `Overwrite` имеет значение `true`, создается файл, в него записывается содержимое, а затем файл закрывается. Если целевой файл уже существует, он будет переопределен. Если `Overwrite` имеет значение `false`, содержимое добавляется к файлу. Если конечный файл не существует, он создается.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В этом примере задача `WriteLinesToFile` используется для записи путей к элементам из коллекции `MyItems` в файл, указанный в коллекции элементов `MyTextFile`.  
  
```xml  
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

В этом примере свойство с внедренными символами новой строки используется для записи текстового файла, содержащего несколько строк. Если запись в `Lines` содержит внедренные символы новой строки, новые строки включаются в выходной файл. Таким образом можно ссылаться на многострочные свойства.

```xml  
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
