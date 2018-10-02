---
title: Задача CreateProperty | Документы Майкрософт
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
manager: ghogen
ms.openlocfilehash: 961f034f2bb508175d258259097f3be25e2a0b11
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571443"
---
# <a name="createproperty-task"></a>Задача CreateProperty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача CreateProperty](https://docs.microsoft.com/visualstudio/msbuild/createproperty-task).  
  
  
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
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)



