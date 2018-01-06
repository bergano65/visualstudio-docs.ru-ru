---
title: "IEnumDebugFields | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields
helpviewer_keywords: IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e930a9e78fb1d91bc5738256e0555f3949829c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс, реализуемый поставщиком символ для предоставления наборы объектов, реализующих [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейса. Обратите внимание, что это не стандартный перечисления COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) метод.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс возвращается [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает следующий набор [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекты из перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает заданное число позиций.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбрасывает перечисления в первую запись.|  
|[Клон](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|  
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