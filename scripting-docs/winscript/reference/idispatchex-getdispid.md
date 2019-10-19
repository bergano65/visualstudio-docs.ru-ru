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
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576605"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Сопоставляет имя одного элемента с соответствующим идентификатором DISPID, который затем можно использовать при последующих вызовах `IDispatchEx::InvokeEx`.  
  
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
  
|значения|Смысл|  
|-----------|-------------|  
|фдекснамекасесенситиве|Запрашивает, что поиск имени выполняется с учетом регистра. Может игнорироваться объектом, который не поддерживает поиск с учетом регистра.|  
|фдекснаминсуре|Запрашивает создание элемента, если он еще не существует. Новый элемент должен быть создан со значением `VT_EMPTY`.|  
|фдекснамеимплиЦит|Указывает, что вызывающий объект выполняет поиск элементов определенного имени, если базовый объект не указан явно.|  
|фдекснамекасеинсенситиве|Запрашивает, что поиск имени выполняется без учета регистра. Может игнорироваться объектом, который не поддерживает поиск без учета регистра.|  
  
 `pid`  
 Указатель на расположение, выделенное вызывающим объектом, для получения результата DISPID. При возникновении ошибки `pid` содержит DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`E_OUTOFMEMORY`|Недостаточно памяти.|  
|`DISP_E_UNKNOWNNAME`|Неизвестное имя.|  
  
## <a name="remarks"></a>Заметки  
 `GetDispID` можно использовать вместо `GetIDsOfNames` для получения идентификатора DISPID для данного элемента.  
  
 Поскольку `IDispatchEx` допускает добавление и удаление элементов, набор идентификаторов DISPID не остается постоянным в течение времени существования объекта.  
  
 Неиспользуемый параметр `riid` в `IDispatch::GetIDsOfNames` был удален.  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)