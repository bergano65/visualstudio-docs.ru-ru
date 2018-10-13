---
title: 'Внутренние элементы: класс TaskScheduler | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e384b9c7734c2197dd79c0b9fb6b415329ae0f05
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203792"
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
  
|Имя|Описание|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Извлекает массив всех запланированных заданий.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Получает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в текущий момент.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

