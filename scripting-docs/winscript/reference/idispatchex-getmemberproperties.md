---
title: IDispatchEx::GetMemberProperties | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f607e06fe3c898a6839c0bbd2d51edee1f0ffb2c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160736"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Извлекает свойства члена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентифицирует член. Использует `GetDispID` или `GetNextDispID` получить идентификатор диспетчеризации.  
  
 `grfdexFetch`  
 Определяет, какие свойства следует извлечь. Это может представлять собой сочетание значений, перечисленных в разделе `pgrfdex` и/или сочетания из следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|grfdexPropCanAll|Объединяет fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct и fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Объединяет fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct и fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Объединяет fdexPropNoSideEffects и fdexPropDynamicType.|  
|grfdexPropAll|Объединяет grfdexPropCanAll, grfdexPropCannotAll и grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Адрес `DWORD` , получающий запрашиваемые свойства. Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexPropCanGet|Элемент можно получить с помощью DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Элемент не удается получить с помощью DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Элемент может быть задан с помощью DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Если элемент не задан с помощью DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Элемент может быть задан с помощью DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Если элемент не задан с помощью DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Элемент не имеет никаких побочных эффектов. Например, отладчик может безопасно get/set/вызова этот член, не изменяя состояние сценария, для которого выполняется отладка.|  
|fdexPropDynamicType|Член является динамическим и можно изменить во время существования объекта.|  
|fdexPropCanCall|Элемент можно вызывать как метод с помощью DISPATCH_METHOD.|  
|fdexPropCannotCall|Элемент нельзя вызывать как метод с помощью DISPATCH_METHOD.|  
|fdexPropCanConstruct|Член может вызываться как конструктор, с помощью DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Элемент не может вызываться как конструктор, с помощью DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Элемент может инициировать события.|  
|fdexPropCannotSourceEvents|Элемент не может порождать события.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`DISP_E_UNKNOWNNAME`|Имя не был известен.|  
  
## <a name="example"></a>Пример  
  
```cpp
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