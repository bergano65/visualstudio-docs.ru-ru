---
title: IDebugFunctionPosition2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4811a6f2aa79e2e19524c0ea1e3e687cd7e28220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180916"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет абстрактное расположение функции в исходном документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс, чтобы представить расположение функции в исходном документе.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс предоставляется как часть объединения [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (в частности, структуры [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ), которая в свою очередь является частью структуры [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , используемой при создании ожидающей точки останова.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugFunctionPosition2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Возвращает имя функции, относительно которой находится эта координата.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Возвращает смещение от начала функции.|  
  
## <a name="remarks"></a>Remarks  
 Расположение, представленное этим интерфейсом, основано на тексте, а именно [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуре.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
