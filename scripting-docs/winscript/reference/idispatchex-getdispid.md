---
title: IDispatchEx::GetDispID | Документация Майкрософт
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
ms.openlocfilehash: 95ab1d72e5b2f608c51ac6e56be1986df8945ec2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152867"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Сопоставляет имя одного элемента с его соответствующий идентификатор DISPID, который затем может использоваться в последующих вызовах `IDispatchEx::InvokeEx`.  
  
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
 Определяет параметры для получения идентификатора элемента. Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexNameCaseSensitive|Запросы, которые выполнить поиск имени регистра. Могут быть проигнорированы в объект, который не поддерживает поиск с учетом регистра.|  
|fdexNameEnsure|Запрашивает, что член создаваться, если он еще не существует. Новый член должен будет создан со значением `VT_EMPTY`.|  
|fdexNameImplicit|Указывает, что вызывающий объект ищет объекты членом определенным именем при базовый объект не указан явно.|  
|fdexNameCaseInsensitive|Запросы, которые при поиске имени выполняться без учета регистра. Могут быть проигнорированы в объект, который не поддерживает поиск без учета регистра.|  
  
 `pid`  
 Указатель на выделенный вызывающим объектом расположение для получения результата DISPID. Если возникает ошибка, `pid` содержит DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`E_OUTOFMEMORY`|Не хватает памяти.|  
|`DISP_E_UNKNOWNNAME`|Имя не был известен.|  
  
## <a name="remarks"></a>Примечания  
 `GetDispID` может использоваться вместо `GetIDsOfNames` получить идентификатор DISPID для данного элемента.  
  
 Так как `IDispatchEx` допускает добавление и удаление элементов, набор идентификаторов DispId не остаются постоянными в течение времени существования объекта.  
  
 Неиспользуемые `riid` параметр в `IDispatch::GetIDsOfNames` был удален.  
  
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