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
ms.openlocfilehash: bb870bcc3c4297d5d1b403176f931f75e418d423
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149714"
---
# <a name="formaturl-task"></a>Задача FormatUrl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Преобразовывает URL-адрес в правильный формат URL-адреса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FormatUrl` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`InputUrl`|Необязательный параметр `String` .<br /><br /> Указывает URL-адрес для форматирования.|  
|`OutputUrl`|Необязательный выходной параметр `String`.<br /><br /> Указывает отформатированный URL-адрес.|  
  
## <a name="remarks"></a>Примечания  
 Кроме параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
