---
title: Задача GetAssemblyIdentity | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b4a578d1d22c6e912fd3f7edc203195dbba8987
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666082"
---
# <a name="getassemblyidentity-task"></a>Задача GetAssemblyIdentity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Извлекает идентификаторы сборок из указанных файлов и выводит сведения об удостоверении.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GetAssemblyIdentity`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Assemblies`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит извлеченные идентификаторы сборок.|  
|`AssemblyFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы, из которых требуется извлечь идентификаторы.|  
  
## <a name="remarks"></a>Примечания  
 Элементы, выводимые параметром `Assemblies`, содержат записи метаданных элементов с именем `Version`, `PublicKeyToken` и `Culture`.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример извлекает идентификатор файлов, указанных в элементе `MyAssemblies`, и выводит их в элемент `MyAssemblyIdentities`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
