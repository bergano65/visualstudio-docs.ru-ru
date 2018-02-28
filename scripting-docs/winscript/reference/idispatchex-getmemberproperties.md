---
title: "IDispatchEx::GetMemberProperties | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Извлекает свойства члена.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` для получения идентификатора диспетчеризации.  
  
 `grfdexFetch`  
 Определяет, какие свойства следует получить. Это может быть сочетанием значений, перечисленных в разделе `pgrfdex` и/или сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|grfdexPropCanAll|Объединяет fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct и fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Объединяет fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct и fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Объединяет fdexPropNoSideEffects и fdexPropDynamicType.|  
|grfdexPropAll|Объединяет grfdexPropCanAll, grfdexPropCannotAll и grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Адрес `DWORD` , который получает запрошенные свойства. Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexPropCanGet|Элемент может быть получен с помощью DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Не удается получить элемент с помощью DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Элемент может быть задан с помощью DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Элемент не может быть задан DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Элемент может быть задан с помощью DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Элемент не может быть задан DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Элемент не имеет никаких побочных эффектов. Например, отладчик может безопасно get/set/вызов этот член, не изменяя состояние скрипта, для которого выполняется отладка.|  
|fdexPropDynamicType|Элемент является динамическим и можно изменить во время существования объекта.|  
|fdexPropCanCall|Элемент можно вызывать как метод с помощью DISPATCH_METHOD.|  
|fdexPropCannotCall|Элемент нельзя вызывать как метод с помощью DISPATCH_METHOD.|  
|fdexPropCanConstruct|Как с помощью DISPATCH_CONSTRUCT конструктор может вызываться члена.|  
|fdexPropCannotConstruct|Элемент не может вызываться как конструктор с помощью DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Элемент может инициировать события.|  
|fdexPropCannotSourceEvents|Элемент не может порождать события.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`DISP_E_UNKNOWNNAME`|Имя не был известен.|  
  
## <a name="example"></a>Пример  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)