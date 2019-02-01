---
title: Задача CreateProperty | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2440d6af45f08a3b53cf531a357cc807d4b22fc7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804457"
---
# <a name="createproperty-task"></a>Задача CreateProperty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Заполняет свойства переданными значениями. Это позволяет копировать значения из одного свойства или строки в другое свойство или строку.  
  
## <a name="attributes"></a>Атрибуты  
 В следующей таблице приводятся параметры задачи `CreateProperty` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Value`|Необязательный выходной параметр `String`.<br /><br /> Указывает значение для копирования в новое свойство.|  
|`ValueSetByTask`|Необязательный выходной параметр `String`.<br /><br /> Содержит то же значение, что и параметр `Value`. Используйте этот параметр только в том случае, если вы не хотите, чтобы [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] задавал выходное свойство при пропуске вложенного целевого объекта из-за актуальных выходных данных.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `CreateProperty`, чтобы создать свойство `NewFile` с помощью сочетания значений свойств `SourceFilename` и `SourceFileExtension`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 После запуска проекта значение свойства `NewFile` равно `Module1.vb`.  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
