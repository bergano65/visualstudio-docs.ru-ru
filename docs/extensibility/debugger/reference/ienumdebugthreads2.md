---
title: IEnumDebugThreads2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Это интерфейса перечисляет поток, выполняемый в текущий сеанс отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления списка потоков в программе.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) получить этот интерфейс, представляющий список всех программ, запущенных в процессе все потоки. Вызовите [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) получить этот интерфейс, представляющий список потоков, выполняющих в программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugThreads2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Извлекает указанное число потоков в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропускает указанное число потоков в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель, с тем же состоянием перечисления, что и текущий.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Возвращает количество потоков в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio обычно получает этот интерфейс для обновления **потоков** окно также для получения списка первый поток для вызова [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md), и [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md)