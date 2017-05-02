---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
Позволяет обработчику скриптов для получения сведений об элементе добавленном с методом [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).  
  
## Синтаксис  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### Параметры  
 `pstrName`  
 \[in\] имя, связанное с элементом, указанным в [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) методом.  
  
 `dwReturnMask`  
 \[in\] определение битовой маски, какие сведения об элементе должно быть возвращено.  Обработчик скриптов должен запросить минимальное возможное количество информации, поскольку некоторые возвращаемых параметров \(например, `ITypeInfo`\) может занять значительное время загрузки или создать.  Может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTINFO\_IUNKNOWN|Возвращает интерфейс `IUnknown` для данного элемента.|  
|SCRIPTINFO\_ITYPEINFO|Возвращает интерфейс `ITypeInfo` для данного элемента.|  
  
 `ppunkItem`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IUnknown`, связанный с заданным элементом.  Обработчик скриптов может использовать метод `IUnknown::QueryInterface` чтобы получить интерфейс `IDispatch` для элемента.  Этот параметр возвращает значение NULL, если `dwReturnMask` не содержит значение SCRIPTINFO\_IUNKNOWN.  Кроме того, он возвращает значение NULL, если отсутствует объект, связанный с именем элемента; этот механизм используется для создания простой класс с именем добавление когда элемент был установлен в SCRIPTITEM\_CODEONLY если пометить метод [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).  
  
 `ppTypeInfo`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `ITypeInfo`, связанные с элементом.  Этот параметр возвращает значение NULL, если `dwReturnMask` не содержит значение SCRIPTINFO\_ITYPEINFO или если сведения о типе недоступна для данного элемента.  Если сведения о типе недоступна, то объект не может события источника и привязку необходимо понимать имени с помощью метода `IDispatch::GetIDsOfNames`.  Обратите внимание, что полученный интерфейс компонентного класса `ITypeInfo` описание элемента \(TKIND\_COCLASS\), поскольку объект может поддерживать несколько интерфейсов и интерфейсы событий.  Если элемент поддерживает интерфейс `IProvideMultipleTypeInfo`, то полученный интерфейс `ITypeInfo` совпадает с нуля индекс `ITypeInfo`, который был бы получен с помощью метода `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`TYPE_E_ELEMENTNOTFOUND`|Элемент с указанным именем не был найден.|  
  
## Заметки  
 Этот метод извлекает только сведения, отображаемые в параметре `dwReturnMask`; это повышает производительность.  Например, если интерфейс `ITypeInfo` не является обязательным для элемента, просто не указано в `dwReturnMask`.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)