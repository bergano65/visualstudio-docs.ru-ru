---
title: IEnumDebugPrograms2 | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: d0277c316329e0adb763eb614f6d453a531781c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877475"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Этот интерфейс перечисляет программ, работающих в текущем сеансе отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список отлаживаемых по DE программ.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) для получения этого интерфейса. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется средой Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPrograms2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает указанное число программ в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает заданное число программ в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Получает количество программ в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio использует этот интерфейс, чтобы:  
  
-   Заполнение **модули** окна (путем вызова [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) и последующего вызова [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) на каждую программу).  
  
-   Заполнение **присоединение к процессу** список (путем вызова `IDebugProcess2::EnumPrograms` и последующего вызова [QueryInterface](/cpp/atl/queryinterface) на каждом [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для получения [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) интерфейс).  
  
-   Создать список DEs, способное отлаживать каждой программы в процессе (с помощью [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Применение обновлений, изменить и продолжить "(ENC) для каждой программы (путем вызова IDebugProcess2::EnumPrograms и последующего вызова [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)