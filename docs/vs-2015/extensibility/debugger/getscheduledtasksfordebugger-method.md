---
title: Метод GetScheduledTasksForDebugger | Документация Майкрософт
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
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3041d21a19ad276ed51e5fdcb9f11ad5468888bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810069"
---
# <a name="getscheduledtasksfordebugger-method"></a>Метод GetScheduledTasksForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает массив всех запланированных заданий.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив всех запланированных задач. Каждая задача выполняется или завершено выполнение.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является потокобезопасным и не должны использоваться параллельно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> его следует вызывать из отладчика, только в том случае, если отладчик приостановил всех остальных потоков.  
  
## <a name="see-also"></a>См. также  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)

