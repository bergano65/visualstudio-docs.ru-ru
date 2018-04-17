---
title: IEnumDebugErrorBreakpoints2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1860b1baf5f5c42b5cf27d4521b29230d447ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Этот интерфейс перечисляет точек останова ошибок, связанных с ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) получить этот интерфейс, представляющий список точек останова, которые не могут быть привязаны или [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) получить этот интерфейс, представляющий список точек останова не были привязаны.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugErrorBreakpoints2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Извлекает указанное число точек останова ошибок в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Пропускает указанное число точек останова ошибок в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Возвращает номер ошибки точки останова в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс содержит список [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейсы, каждая из которых описывает точку останова, не удалось выполнить привязку, и почему он не удалось выполнить привязку. Visual Studio использует `IEnumDebugErrorBreakpoint2` интерфейса для обновления точки останова отображается в Интегрированной среде разработки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)