---
title: 'Внутренние элементы: класс TaskScheduler | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990494"
---
# <a name="taskscheduler-class---internal-members"></a>Внутренние элементы: класс TaskScheduler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом разделе описывается внутренним членам объектов <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класс, который помогут вам реализовать пользовательского отладчика. Общие сведения об этом классе см. в разделе <xref:System.Threading.Tasks.TaskScheduler> справочника.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|name|Описание|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Извлекает массив всех запланированных заданий.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Получает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в текущий момент.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
