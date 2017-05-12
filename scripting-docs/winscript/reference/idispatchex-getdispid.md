---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID — метод"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
Сопоставляет имя одиночной к соответствующему DISPID, которое можно использовать при последующих вызовах `IDispatchEx::InvokeEx`.  
  
## Синтаксис  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### Параметры  
 `bstrName`  
 Переданный в имя сопоставляемого.  
  
 `grfdex`  
 Определяет параметры для получения идентификатор элемента.  Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|fdexNameCaseSensitive|Запросы, которые были внесены в поиск имени учитывающем регистр образом.  Может быть игнорироватьо объектом, который не поддерживает поиск с учетом регистра.|  
|fdexNameEnsure|Запросы, участнику создал если он еще не существует.  Новый элемент следует создать со значением `VT_EMPTY`.|  
|fdexNameImplicit|Указывает, что участник выполняет поиск объектов для элемента указанного имени, когда базовый объект не был определен явно.|  
|fdexNameCaseInsensitive|Запросы, которые были внесены в поиск имени обращение\- нечувствительном образом.  Может быть игнорироватьо объектом, который не поддерживает обращение\- поиск символов не учитывается.|  
  
 `pid`  
 Указатель на абонент\- выбранном месте для получения результата DISPID.  Если ошибка возникает `pid` содержит DISPID\_UNKNOWN.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|`E_OUTOFMEMORY`|Недостаточно памяти.|  
|`DISP_E_UNKNOWNNAME`|Имя не было известно.|  
  
## Заметки  
 `GetDispID` можно использовать вместо `GetIDsOfNames` чтобы получить идентификатор DISPID для заданного элемента.  
  
 Поскольку `IDispatchEx` допускает добавление и удаление членов, набор идентификаторов dispid не остается постоянным в течение времени существования объекта.  
  
 Неиспользуемый параметр `riid` в `IDispatch::GetIDsOfNames` был удален.  
  
## Пример  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)