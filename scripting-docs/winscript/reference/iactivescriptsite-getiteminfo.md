---
title: 'IActiveScriptSite:: GetItemInfo | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570924"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Позволяет обработчику скриптов получать сведения об элементе, добавленном с помощью метода [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrName`  
 окне Имя, связанное с элементом, как указано в методе [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 окне Битовая маска, указывающая, какие сведения об элементе следует вернуть. Обработчик скриптов должен запрашивать минимальный объем информации, так как некоторые из возвращаемых параметров (например `ITypeInfo`) могут занимать значительное время для загрузки или создания. Может быть сочетанием следующих значений:  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Возвращает интерфейс `IUnknown` для этого элемента.|  
|SCRIPTINFO_ITYPEINFO|Возвращает интерфейс `ITypeInfo` для этого элемента.|  
  
 `ppunkItem`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IUnknown`, связанный с данным элементом. Обработчик скриптов может использовать метод `IUnknown::QueryInterface` для получения интерфейса `IDispatch` для элемента. Этот параметр получает значение NULL, если `dwReturnMask` не включает значение SCRIPTINFO_IUNKNOWN. Кроме того, он получает значение NULL, если отсутствует объект, связанный с именем элемента. Этот механизм используется для создания простого класса при добавлении именованного элемента с флагом SCRIPTITEM_CODEONLY, установленным в методе [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `ITypeInfo`, связанный с элементом. Этот параметр получает значение NULL, если `dwReturnMask` не содержит значение SCRIPTINFO_ITYPEINFO, или если сведения о типе недоступны для этого элемента. Если сведения о типе недоступны, объект не может быть источником событий, а привязка имени должна быть реализована с помощью метода `IDispatch::GetIDsOfNames`. Обратите внимание, что извлеченный интерфейс `ITypeInfo` описывает компонентный класс элемента (TKIND_COCLASS), поскольку объект может поддерживать несколько интерфейсов и интерфейсов событий. Если элемент поддерживает интерфейс `IProvideMultipleTypeInfo`, полученный `ITypeInfo` интерфейс совпадает с нулевым индексом `ITypeInfo`, который будет получен с помощью метода `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`TYPE_E_ELEMENTNOTFOUND`|Элемент с указанным именем не найден.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод извлекает только сведения, указанные параметром `dwReturnMask`. Это повышает производительность. Например, если для элемента не требуется интерфейс `ITypeInfo`, он просто не указывается в `dwReturnMask`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)