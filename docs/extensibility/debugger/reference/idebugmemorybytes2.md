---
title: IDebugMemoryBytes2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a738ecb042fa423cf165a42a9d472e06f23648d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887189"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Этот интерфейс представляет байт памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления байтов в памяти.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) возвращает этот интерфейс для предоставления доступа к системной памяти. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) и [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) возвращают этот интерфейс для предоставления доступа к объекта байтов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugMemoryBytes2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Считывает последовательность байтов, начиная с заданного расположения.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Записывает `dwCount` байт, начиная с `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Возвращает размер в байтах, памяти, представленного этим интерфейсом.|  
  
## <a name="remarks"></a>Примечания  
 Для свойств [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) предоставляет интерфейс, представляющий массив `IDebugMemoryBytes2` интерфейс для доступа к значениям в этом массиве.  
  
 Visual Studio **представление памяти** вызовы [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) извлекаемого `IDebugMemoryBytes2` интерфейс для доступа к системной памяти. Получение адреса для доступа, синтаксический анализ выражения, введенные в виде адреса в памяти представление и затем оценивая проанализированное выражение, использующее [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для получения `IDebugProperty2` интерфейс. Вызов [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) возвращает [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , описывающий адрес памяти. Затем передается этот контекст памяти [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)