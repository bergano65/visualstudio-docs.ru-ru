---
title: Иенумдебугфиелдс | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e3c9a43b6903522fe2caf0e329f8e8faa69cd6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161091"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет коллекцию объектов, реализующих интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщиком символов для предоставления наборов объектов, реализующих интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) . Обратите внимание, что это не стандартное перечисление COM из-за наличия метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс возвращается [жетмесодфиелдсбинаме](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [жетнамеспацесуседатаддресс](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает из перечисления следующий набор объектов [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает указанное число записей.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбрасывает перечисление до первой записи.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Возвращает количество записей в перечислении.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [жетмесодфиелдсбинаме](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
