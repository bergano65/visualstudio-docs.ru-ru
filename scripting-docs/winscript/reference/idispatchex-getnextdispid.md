---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID — метод"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
Перечисляет члены объекта.  
  
## Синтаксис  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### Параметры  
 `grfdex`  
 Указывает, какой набор элементов необходимо перечислить.  Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|fdexEnumDefault|Запросы, что объект перечисляет элементы по умолчанию.  Объект разрешения для перечисления любого набора элементов.|  
|fdexEnumAll|Запросы, что объект перечисляет все элементы.  Объект разрешения для перечисления любого набора элементов.|  
  
 `id`  
 Определяет текущий элемент.  Извлекает элемент GetNextDispID в перечислении после данного объекта.  Использование GetDispID или предыдущий вызов GetNextDispID получить этот идентификатор.  Использует значение DISPID\_STARTENUM, чтобы получить первый идентификатор первого элемента.  
  
 `pid`  
 Адрес переменной DISPID, которая возвращает идентификатор следующего элемента в перечислении.  
  
 Если член является удаление `DeleteMemberByName` или `DeleteMemberByDispID`, то необходимости `DISPID` оставаться допустимыми для `GetNextDispID`.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|`S_FALSE`|Перечисление выполняется.|  
  
## Пример  
  
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
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)