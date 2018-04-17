---
title: IEnumDebugAddresses | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: bfed705253a03ec550e7533f7e2ab323b7ead62a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс, реализуемый поставщиком символ для предоставления наборы объектов, реализующих [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейса. Обратите внимание, что это не стандартный перечисления COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс возвращается [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Извлекает следующий набор [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Пропускает заданное число позиций.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сбрасывает перечисления в первую запись.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Возвращает число элементов перечисления.|  
  
## <a name="remarks"></a>Примечания  
 Обычно этот интерфейс используется подсистема отладки для определения соответствующего адреса нужно присвоить средство оценки выражений.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)