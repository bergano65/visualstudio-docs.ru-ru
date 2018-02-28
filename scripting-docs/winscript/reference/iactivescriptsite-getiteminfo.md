---
title: "IActiveScriptSite::GetItemInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Позволяет обработчику сценариев для получения сведений об элементе добавлены с классом [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrName`  
 [in] Имя, связанное с элементом, как указано в [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
 `dwReturnMask`  
 [in] Битовая маска, указывающая, какие сведения об элементе должны возвращаться. Обработчик скриптов следует запрашивать минимальный объем информации, так как некоторые возвращаемые параметры (например, `ITypeInfo`) может занять значительное время, чтобы загрузить или создать. Может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Возвращает `IUnknown` интерфейс для этого элемента.|  
|SCRIPTINFO_ITYPEINFO|Возвращает `ITypeInfo` интерфейс для этого элемента.|  
  
 `ppunkItem`  
 [out] Адрес переменной, которая получает указатель на `IUnknown` интерфейса, связанного с данного элемента. Обработчик скриптов можно использовать `IUnknown::QueryInterface` метод, чтобы получить `IDispatch` интерфейса для элемента. Этот параметр получает значение NULL, если `dwReturnMask` не содержит значения SCRIPTINFO_IUNKNOWN. Кроме того он получает значение NULL, если нет объекта, связанный с именем элемента. Этот механизм используется для создания простого класса при добавлении флага SCRIPTITEM_CODEONLY задано именованный элемент [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
 `ppTypeInfo`  
 [out] Адрес переменной, которая получает указатель на `ITypeInfo` интерфейса, связанного с элементом. Этот параметр получает значение NULL, если `dwReturnMask` не содержит значение SCRIPTINFO_ITYPEINFO или если сведения о типе для этого элемента недоступен. Если сведения о типе недоступна, объект не может быть источником событий и привязки имени должна быть реализована с `IDispatch::GetIDsOfNames` метод. Обратите внимание, что `ITypeInfo` получить интерфейс описывает компонентного класса элемента (TKIND_COCLASS), так как объект может поддерживать несколько интерфейсов и интерфейсах событий. Если элемент поддерживает `IProvideMultipleTypeInfo` интерфейс, `ITypeInfo` получить интерфейс совпадает с нулевым индексом `ITypeInfo` , был бы получен с помощью `IProvideMultipleTypeInfo::GetInfoOfIndex` метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`TYPE_E_ELEMENTNOTFOUND`|Элемент с указанным именем не найден.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает только данные, обозначенном `dwReturnMask` параметр; это повышает производительность. Например если `ITypeInfo` интерфейса не нужны для элемента, он просто не указан в `dwReturnMask`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)