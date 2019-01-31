---
title: Задача FormatUrl | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6f3118515d023f9f57d4578d042a0fa5a702872
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803348"
---
# <a name="formaturl-task"></a>Задача FormatUrl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Преобразовывает URL-адрес в правильный формат URL-адреса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FormatUrl` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`InputUrl`|Необязательный параметр `String` .<br /><br /> Указывает URL-адрес для форматирования.|  
|`OutputUrl`|Необязательный выходной параметр `String`.<br /><br /> Указывает отформатированный URL-адрес.|  
  
## <a name="remarks"></a>Примечания  
 Кроме параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
