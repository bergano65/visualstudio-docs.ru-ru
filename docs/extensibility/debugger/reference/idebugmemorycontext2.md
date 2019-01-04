---
title: IDebugMemoryContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: acd36140d4624c2002b28f2d7932931817f46f56
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870798"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Этот интерфейс представляет позицию в адресном пространстве машины, работающей в отлаживаемую программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления на адрес в памяти.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) или [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) возвращает этот интерфейс. Кроме того, вызовы [добавить](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) и [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) возвращают новые копии этого интерфейса, после применения соответствующих арифметической операции.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugMemoryContext2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Получает имя, отображаемое для пользователя для данного контекста.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Возвращает сведения, описывающие этот контекст.|  
|[Добавить](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Добавляет указанное значение к адресу текущий контекст для создания нового контекста.|  
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Вычитает указанное значение из адреса текущий контекст для создания нового контекста.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Сравнивает два контекста так, как указано в сравнение флагов.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio **памяти** вызовы в окна [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) для получения `IDebugMemoryContext2` интерфейса, который содержит вычисленное выражение, используемое для адреса памяти. Этот контекст передается [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) для указания адреса для чтения или записи.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)