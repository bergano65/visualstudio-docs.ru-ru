---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName — метод"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
Удаляет член именем.  
  
## Синтаксис  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### Параметры  
 `bstrName`  
 Имя элемента для удаления.  
  
 `grfdex`  
 Определяет, если имя с учетом регистра.  Это может быть одно из следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|fdexNameCaseSensitive|Запросы, которые были внесены в поиск имени учитывающем регистр образом.  Может быть игнорироватьо объектом, который не поддерживает поиск с учетом регистра.|  
|fdexNameCaseInsensitive|Запросы, которые были внесены в поиск имени обращение\- нечувствительном образом.  Может быть игнорироватьо объектом, который не поддерживает обращение\- поиск символов не учитывается.|  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Успех.|  
|`S_FALSE`|Элемент существует, но не может быть удалена.|  
  
## Заметки  
 Если элемент удален, то идентификатор DISPID должны оставаться допустимыми для `GetNextDispID`.  
  
 Если элемент с заданным именем удаление и более поздних версий элемент создается повторно с тем же именем, то идентификатор DISPID должен быть одинаковым.  \(Ли элементы, отличающиеся только регистр "одинаковое" объект\- зависимые\).  
  
## Пример  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)