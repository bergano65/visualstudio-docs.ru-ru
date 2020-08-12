---
title: 'IDispatchEx:: Жетдиспид | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144537"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Сопоставляет имя одного элемента с соответствующим идентификатором DISPID, который затем может использоваться при последующих вызовах метода `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 Переданное имя для сопоставления.  
  
 `grfdex`  
 Определяет параметры получения идентификатора элемента. Это может быть сочетание следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|фдекснамекасесенситиве|Запрашивает, что поиск имени выполняется с учетом регистра. Может игнорироваться объектом, который не поддерживает поиск с учетом регистра.|  
|фдекснаминсуре|Запрашивает создание элемента, если он еще не существует. Новый элемент должен быть создан со значением `VT_EMPTY` .|  
|фдекснамеимплиЦит|Указывает, что вызывающий объект выполняет поиск элементов определенного имени, если базовый объект не указан явно.|  
|фдекснамекасеинсенситиве|Запрашивает, что поиск имени выполняется без учета регистра. Может игнорироваться объектом, который не поддерживает поиск без учета регистра.|  
  
 `pid`  
 Указатель на расположение, выделенное вызывающим объектом, для получения результата DISPID. При возникновении ошибки `pid` содержит DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|
|-|-|  
|`S_OK`|Успех.|  
|`E_OUTOFMEMORY`|Недостаточно памяти.|  
|`DISP_E_UNKNOWNNAME`|Неизвестное имя.|  
  
## <a name="remarks"></a>Remarks  
 `GetDispID`можно использовать вместо `GetIDsOfNames` для получения DISPID для данного элемента.  
  
 Поскольку `IDispatchEx` позволяет добавлять и удалять члены, набор идентификаторов DISPID не остается постоянным в течение времени существования объекта.  
  
 Неиспользованный `riid` параметр в `IDispatch::GetIDsOfNames` был удален.  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)