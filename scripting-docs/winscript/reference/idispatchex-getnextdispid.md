---
title: IDispatchEx::GetNextDispID | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ece7bde3230da370c8434cef7f780a92604df34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728524"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Перечисляет элементы объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `grfdex`  
 Определяет, какой набор элементов для перечисления. Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexEnumDefault|Запросы, что объект перечисляет элементы по умолчанию. Объект может перечислить любого набора элементов.|  
|fdexEnumAll|Запросы, что объект перечисляет все элементы. Объект может перечислить любого набора элементов.|  
  
 `id`  
 Определяет текущий элемент. Getnextdispid — извлекает элемент из перечисления за первым. Использует getdispid — или предыдущим вызовом getnextdispid — для получения идентификатора. Значение DISPID_STARTENUM используется для получения первого идентификатора первого элемента.  
  
 `pid`  
 Адрес переменной DISPID, которая получает идентификатор следующего элемента в перечислении.  
  
 Если удаляется элемент `DeleteMemberByName` или `DeleteMemberByDispID`, `DISPID` должен оставаться действительным для `GetNextDispID`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`S_FALSE`|Выполняется перечисление.|  
  
## <a name="example"></a>Пример  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)