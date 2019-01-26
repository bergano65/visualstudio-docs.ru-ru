---
title: IEnumDebugThreads2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21a87d4f6005a2ebf0339d8e4bfd20c6fcef423
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917280"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Этого интерфейса перечисляет поток, выполняемый в текущий сеанс отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) для получения этого интерфейса, представляющий список всех потоков во всех программах, выполняющийся в процессе. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) для получения этого интерфейса, представляющий список потоков, выполняющих в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugThreads2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Получает количество потоков в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio обычно получает этот интерфейс для обновления **потоков** окно также, как получить первый поток списка, чтобы вызвать [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md), и [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)