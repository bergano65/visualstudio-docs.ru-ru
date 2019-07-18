---
title: IDebugProgramNodeAttach2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 580d4d2432a957bae8c590b3590a11b1a0b5e84e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148529"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Позволяет узлу программы для получения уведомлений об попытка присоединить соответствующую программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется для одного класса, реализующего [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, чтобы получать уведомления об операции присоединения и предоставляют возможность отменить операцию присоединения.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Получить этот интерфейс, вызвав `QueryInterface` метод в [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекта. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен вызываться перед [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод, чтобы предоставить возможность остановить этот процесс на узле программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Присоединяется к соответствующую программу или откладывает процесс присоединения к [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является предпочтительным вариантом для устаревших [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) метод. Все модули отладки, всегда загружаются с `CoCreateInstance` функции, то есть они создаются вне адресного пространства отлаживаемой программы.  
  
 Если предыдущей реализации `IDebugProgramNode2::Attach_V7` метод просто устанавливает `GUID` из отлаживаемой программы, затем только [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен быть реализован.  
  
 Если предыдущей реализации `IDebugProgramNode2::Attach_V7` метод, используемый интерфейс обратного вызова, который был предоставлен, то эта функциональность должна переместиться на реализацию [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод и `IDebugProgramNodeAttach2` не поддерживает интерфейс должен быть реализован.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
