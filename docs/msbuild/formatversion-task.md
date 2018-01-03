---
title: "Задача FormatVersion | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5e67ca95e7a0cf4750f5e4a77cc4b19ca6a64dd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="formatversion-task"></a>Задача FormatVersion
Добавляет номер редакции к номеру версии.  
  
-   Случай 1. Input: Version=\<не определена>;  Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"  
  
-   Случай 2. Входные данные: Version="1.0.0.*"  Revision="5"; выходные данные: OutputVersion="1.0.0.5"  
  
-   Случай 3. Входные данные: Version="1.0.0.0"  Revision=\<неважно>; выходные данные: OutputVersion="1.0.0.0"  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FormatVersion` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`FormatType`|Необязательный параметр `String` .<br /><br /> Определяет тип формата.<br /><br /> — "Version" = версия.<br />— "Path" = замените "." на "_".|  
|`OutputVersion`|Необязательный выходной параметр `String`.<br /><br /> Указывает выходную версию, содержащую номер редакции.|  
|`Revision`|Необязательный параметр `Int32` .<br /><br /> Указывает редакцию, добавляемую к версии.|  
|`Version`|Необязательный параметр `String` .<br /><br /> Указывает строку номера версии для форматирования.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)