---
title: "Задача VCMessage | Microsoft Docs"
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
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), VCMessage - задача"
  - "VCMessage - задача (MSBuild (Visual C++))"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача VCMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Журналы предупреждений и сообщений об ошибках во время построения.  
  
## Заметки  
 Эта задача позволяет реализовать MSBuild для Visual C\+\+ и не предназначена для вызова пользователем.  Дополнительные сведения см. в разделе <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Параметры  
 В следующей таблице описаны параметры задачи **VCMessage** .  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Arguments**|Необязательный параметр типа **String**.<br /><br /> Разделенный точками с запятой список сообщений для отображения.|  
|**Code**|Обязательный параметр типа **String**.<br /><br /> Номер ошибки, определяющий сообщение.|  
|**Type**|Необязательный параметр типа **String**.<br /><br /> Определяет тип передаваемого сообщения.  Укажите либо `"Предупреждение"` для выдачи предупреждающего сообщения, либо `"Ошибка"` для выдачи сообщения об ошибке.|  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)