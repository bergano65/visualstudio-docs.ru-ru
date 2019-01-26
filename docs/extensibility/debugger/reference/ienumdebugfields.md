---
title: IEnumDebugFields | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4f95ef4dba92baffb15723d5e140b15fece4f23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946026"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщиком символ для предоставления наборы объектов, реализующих [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс. Обратите внимание, что это не стандартные перечисление COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс возвращается [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает следующий набор [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает заданное число позиций.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбрасывает перечисление к первой записи.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Возвращает число элементов перечисления.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)