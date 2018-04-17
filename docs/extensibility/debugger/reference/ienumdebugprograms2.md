---
title: IEnumDebugPrograms2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e95996a0548dcf81957dad60c3e6f73b3424c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Этот интерфейс перечисляет программы, запущенные в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для предоставления списка по DE отлаживаемых программ.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется в Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное число программ в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает указанное число программ в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Возвращает количество программ в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс для:  
  
-   Заполнение **модули** окна (путем вызова [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) и последующего вызова [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) на каждой программы).  
  
-   Заполнение **присоединиться к процессу** список (путем вызова `IDebugProcess2::EnumPrograms` и последующего вызова [QueryInterface](/cpp/atl/queryinterface) на каждом [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для получения [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) интерфейс).  
  
-   Создать список DEs, можно отлаживать каждой программы в процессе (с помощью [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Применить обновления, изменить и продолжить (ENC) для каждой программы (путем вызова IDebugProcess2::EnumPrograms и последующего вызова [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)