---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties — метод"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
Возвращает свойства элемента.  
  
## Синтаксис  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### Параметры  
 `id`  
 Идентифицирует член.  Использование `GetDispID` или `GetNextDispID` получить идентификатор диспетчера.  
  
 `grfdexFetch`  
 Определяет, извлекаемого свойства.  Это может оказаться сочетание значений, перечисленных в `pgrfdex` или сочетанием следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|grfdexPropCanAll|Объединяет fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct и fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Объединяет fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct и fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects и fdexPropDynamicType зернокомбайнов.|  
|grfdexPropAll|Объединяет grfdexPropCanAll, grfdexPropCannotAll и grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Адрес `DWORD`, получающий запрошенного свойства.  Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|fdexPropCanGet|Член может быть получен с помощью DISPATCH\_PROPERTYGET.|  
|fdexPropCannotGet|Член не может быть получен с помощью DISPATCH\_PROPERTYGET.|  
|fdexPropCanPut|Элемент можно задать с помощью DISPATCH\_PROPERTYPUT.|  
|fdexPropCannotPut|Не удается установить с помощью элемента DISPATCH\_PROPERTYPUT.|  
|fdexPropCanPutRef|Элемент можно задать с помощью DISPATCH\_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Не удается установить с помощью элемента DISPATCH\_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Член не имеет побочных эффектов.  Например, отладчик может безопасно получить\/набор и вызов этот элемент без изменения состояния отлаживаемой скрипта.|  
|fdexPropDynamicType|Член является динамическим и может изменяться во время существования объекта.|  
|fdexPropCanCall|Член может вызывать метод с помощью DISPATCH\_METHOD.|  
|fdexPropCannotCall|Элемент нельзя вызывать метод с помощью DISPATCH\_METHOD.|  
|fdexPropCanConstruct|Член может быть вызван, как конструктор с помощью DISPATCH\_CONSTRUCT.|  
|fdexPropCannotConstruct|Член не может быть вызван, как конструктор с помощью DISPATCH\_CONSTRUCT.|  
|fdexPropCanSourceEvents|Получатель прав может создать события.|  
|fdexPropCannotSourceEvents|Элемент не может создать события.|  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|`DISP_E_UNKNOWNNAME`|Имя не было известно.|  
  
## Пример  
  
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
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)