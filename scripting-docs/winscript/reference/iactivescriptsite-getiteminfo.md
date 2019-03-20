---
title: IActiveScriptSite::GetItemInfo | Документация Майкрософт
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
ms.openlocfilehash: 997245f8e4fd43ac2162587f07e4c8711af7caac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148689"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Позволяет обработчику сценариев для получения сведений об элементе добавлены с классом [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
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
 [in] Имя, связанное с элементом, как указано в [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
 `dwReturnMask`  
 [in] Битовая маска, указывающая, какие сведения об элементе должны быть возвращены. Обработчик скриптов должен запросить минимальный объем информации, которые невозможно, так как некоторые возвращаемые параметры (например, `ITypeInfo`) может занимать много времени, чтобы загрузить или создать. Может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Возвращает `IUnknown` интерфейс для этого элемента.|  
|SCRIPTINFO_ITYPEINFO|Возвращает `ITypeInfo` интерфейс для этого элемента.|  
  
 `ppunkItem`  
 [out] Адрес переменной, которая получает указатель на `IUnknown` интерфейса, связанного с данного элемента. Можно использовать обработчик скриптов `IUnknown::QueryInterface` метод, чтобы получить `IDispatch` интерфейса для элемента. Этот параметр принимает значение NULL, если `dwReturnMask` не включает значение SCRIPTINFO_IUNKNOWN. Кроме того он получает значение NULL, если отсутствует объект, связанный с именем элемента. Этот механизм используется для создания простой класс, если именованный элемент был добавлен с флагом SCRIPTITEM_CODEONLY, установленным [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) метод.  
  
 `ppTypeInfo`  
 [out] Адрес переменной, которая получает указатель на `ITypeInfo` интерфейса, связанного с элементом. Этот параметр принимает значение NULL, если `dwReturnMask` не включает значение SCRIPTINFO_ITYPEINFO, или если сведения о типе недоступна для этого элемента. Если сведения о типе недоступна, объект не может быть источником событий и привязки имени должна быть реализована с помощью `IDispatch::GetIDsOfNames` метод. Обратите внимание, что `ITypeInfo` извлечь интерфейс описывает компонентного класса элемента (TKIND_COCLASS), так как объект может поддерживать несколько интерфейсов и интерфейсах событий. Если элемент поддерживает `IProvideMultipleTypeInfo` интерфейс, `ITypeInfo` извлечь интерфейс совпадает с нулевым индексом `ITypeInfo` , был бы получен с помощью `IProvideMultipleTypeInfo::GetInfoOfIndex` метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`TYPE_E_ELEMENTNOTFOUND`|Элемент с указанным именем не найден.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает только данные, обозначается `dwReturnMask` параметр; это повышает производительность. Например если `ITypeInfo` интерфейс не требуется для элемента, он просто не указывается в `dwReturnMask`.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)