---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID — метод"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
Удаляет член DISPID.  
  
## Синтаксис  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### Параметры  
 `id`  
 Идентификатор элемента.  Использование `GetDispID` или `GetNextDispID` получить идентификатор диспетчера.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|`S_FALSE`|Элемент существует, но не может быть удалена.|  
  
## Заметки  
 Если элемент удален, то идентификатор DISPID должны оставаться допустимыми для `GetNextDispID`.  
  
 Если элемент с заданным именем удаление и более поздних версий элемент создается повторно с тем же именем, то идентификатор DISPID должен быть одинаковым.  \(Как имена, которые отличаются только регистр "одинаковое" объект\- зависимые\).  
  
## Пример  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)