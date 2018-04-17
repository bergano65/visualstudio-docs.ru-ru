---
title: IEnumDebugFrameInfo2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Этот интерфейс перечисляет [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы предоставить список структур, описывающий текущий стек вызовов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения этого интерфейса всякий раз, когда точки останова, исключение, или остановка происходит в отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugFrameInfo2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Извлекает указанное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Пропускает указанное число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Возвращает число [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio получает этот интерфейс как первый шаг при обработке точки останова, исключения или приостановить созданным пользователем для отлаживаемой программы. Список [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры представляет текущий стек вызовов, с текущим вызовом функции в начале списка и старые функции вызова в конце списка. Каждый `FRAMEINFO` представляет кадр стека контекста, в котором выражения и просматривать локальные переменные во.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)