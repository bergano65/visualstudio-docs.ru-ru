---
title: IEnumDebugAddresses | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0958ddb9aca23da5f73bd2686f86d8a0ccd826b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920489"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщиком символ для предоставления наборы объектов, реализующих [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс. Обратите внимание, что это не стандартные перечисление COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс возвращается [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Извлекает следующий набор [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Пропускает заданное число позиций.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сбрасывает перечисление к первой записи.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Возвращает число элементов перечисления.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс обычно используется ядром отладки, чтобы определить соответствующий адрес, чтобы предоставить средству оценки выражений.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)