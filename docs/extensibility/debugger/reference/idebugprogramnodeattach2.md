---
title: IDebugProgramNodeAttach2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a83f5635dfacb638a2e76054dc5ed4e887e2a3cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120693"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Позволяет узлу программы для получения уведомлений об попытка подключения к соответствующую программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется в том же классе, который реализует [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, чтобы получать уведомления об операции присоединения и предоставляют возможность отменить операцию присоединения.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получить этот интерфейс, вызвав `QueryInterface` метод в [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекта. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен вызываться перед [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод, чтобы предоставить возможность остановить процесс присоединения узла программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Присоединяет к соответствующую программу или откладывает процесс присоединения к [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс является предпочтительным альтернативным методом устаревшие [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) метод. Все модули отладки, всегда загружаются с `CoCreateInstance` функции, то есть они созданы вне адресного пространства из отлаживаемой программы.  
  
 Если в предыдущей реализации `IDebugProgramNode2::Attach_V7` метод простого задания `GUID` из отлаживаемой программы, затем только [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен быть реализован.  
  
 Если в предыдущей реализации `IDebugProgramNode2::Attach_V7` метод использовать интерфейс обратного вызова, который был предоставлен, то эта функция должна переместиться на реализацию [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод и `IDebugProgramNodeAttach2` не поддерживает интерфейс должен быть реализован.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)