---
title: "IEnumDebugErrorBreakpoints2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 39b2ce4bb8fdecbe67d6c39e53454e49853f55c8
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Этот интерфейс перечисляет точек останова ошибок, связанных с ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Отладчик (DE) реализует этот интерфейс как часть поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Visual Studio вызывает [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) получить этот интерфейс, представляющий список точек останова, не может быть привязана, или [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) получить этот интерфейс, представляющий список точек останова, которые не были связаны.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugErrorBreakpoints2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Получает указанное количество точек останова ошибок в последовательность перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Пропускает указанное число точек останова ошибок в последовательность перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Создает перечислитель с тем же состоянием, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Возвращает число точек останова ошибок в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс содержит список [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейсов, каждый из которых описывает точку останова, не удалось выполнить привязку и почему ее не удалось выполнить привязку. Visual Studio использует `IEnumDebugErrorBreakpoint2` интерфейс для обновления точки останова, показанный в Интегрированной среде разработки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
