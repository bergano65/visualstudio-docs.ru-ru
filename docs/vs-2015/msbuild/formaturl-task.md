---
title: Задача FormatUrl | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0dce78ba9e81e5b568557fd963fb7480904ff2da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560898"
---
# <a name="formaturl-task"></a>Задача FormatUrl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача FormatUrl](https://docs.microsoft.com/visualstudio/msbuild/formaturl-task).  
  
  
Преобразовывает URL-адрес в правильный формат URL-адреса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FormatUrl` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`InputUrl`|Необязательный параметр `String` .<br /><br /> Указывает URL-адрес для форматирования.|  
|`OutputUrl`|Необязательный выходной параметр `String`.<br /><br /> Указывает отформатированный URL-адрес.|  
  
## <a name="remarks"></a>Примечания  
 Кроме параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



