---
title: Задача GetReferenceAssemblyPaths | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f771f3c769ea41979210058a58dc1d0d125a4ffe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149478"
---
# <a name="getreferenceassemblypaths-task"></a>Задача GetReferenceAssemblyPaths
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возвращает пути к эталонным сборкам для различных версий .NET Framework.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `GetReferenceAssemblyPaths` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Необязательный выходной параметр `String[]`.<br /><br /> Возвращает путь на основе параметра `TargetFrameworkMoniker`. Если `TargetFrameworkMoniker` равен NULL или пуст, этот путь имеет значение `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Необязательный выходной параметр `String[]`.<br /><br /> Возвращает путь на основе параметра `TargetFrameworkMoniker` без учета профильной части моникера. Если `TargetFrameworkMoniker` равен NULL или пуст, этот путь имеет значение `String.Empty`.|  
|`TargetFrameworkMoniker`|Необязательный параметр `String` .<br /><br /> Указывает моникер целевой платформы, связанный с путями базовых сборок.|  
|`RootPath`|Необязательный параметр `String` .<br /><br /> Указывает корневой путь, используемый для создания пути базовой сборки.|  
|`BypassFrameworkInstallChecks`|Необязательный (логический<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) параметр.<br /><br /> Если задано значение `true`, обходит основные проверки, которые `GetReferenceAssemblyPaths` выполняет по умолчанию, чтобы убедиться в установке определенных платформ среды выполнения, в зависимости от целевой платформы.|  
|`TargetFrameworkMonikerDisplayName`|Необязательный выходной параметр `String`.<br /><br /> Задает отображаемое имя для моникера целевой платформы.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
