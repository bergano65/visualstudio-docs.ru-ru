---
title: IEnumDebugErrorBreakpoints2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9ffe2d65f2a087d0b65cc4f122d446b0704924f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570008"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEnumDebugErrorBreakpoints2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugerrorbreakpoints2).  
  
Этот интерфейс перечисляет точек останова ошибок, связанных с ожидающая точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Visual Studio вызывает [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) для получения этого интерфейса, представляющий список точек останова, которые не удается найти метод, или [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) для получения этого интерфейса, представляющий список точек останова не были привязаны.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugErrorBreakpoints2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Извлекает указанное число точек останова ошибок в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Пропускает заданное число точек останова ошибок в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Получает номер ошибки точки останова в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс содержит список [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейсов, каждый из которых описывает точку останова, не удалось выполнить привязку и почему он не удалось выполнить привязку. Visual Studio использует `IEnumDebugErrorBreakpoint2` интерфейса для обновления точки останова, показанный в интегрированной среде разработки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

