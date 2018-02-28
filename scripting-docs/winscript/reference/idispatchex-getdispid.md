---
title: "IDispatchEx::GetDispID | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Сопоставляет имя одного элемента с его соответствующий DISPID, который можно использовать при последующих вызовах `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 Переданный имени должен быть сопоставлен.  
  
 `grfdex`  
 Определяет параметры для получения идентификатора элемента. Это может быть сочетанием следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexNameCaseSensitive|Запросы, которые выполнить поиск имени регистра. Могут игнорироваться объектом, который не поддерживает поиск с учетом регистра.|  
|fdexNameEnsure|Запрашивает, создать элемент, если он еще не существует. Необходимо создать новый член с значение `VT_EMPTY`.|  
|fdexNameImplicit|Указывает, что вызывающий объект поиск один или несколько объектов членом определенным именем при базовый объект не указан явно.|  
|fdexNameCaseInsensitive|Запросы, которые выполнить поиск имени регистра. Могут игнорироваться объектом, который не поддерживает поиск без учета регистра.|  
  
 `pid`  
 Указатель на расположение, выделенный вызывающим объектом, для получения результата DISPID. При возникновении ошибки `pid` содержит DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`E_OUTOFMEMORY`|Не хватает памяти.|  
|`DISP_E_UNKNOWNNAME`|Имя не был известен.|  
  
## <a name="remarks"></a>Примечания  
 `GetDispID`может быть использован вместо `GetIDsOfNames` получить идентификатор DISPID для данного элемента.  
  
 Поскольку `IDispatchEx` допускает добавление и удаление элементов в наборе DISPID не остаются постоянными в течение времени существования объекта.  
  
 Неиспользуемые `riid` параметр в `IDispatch::GetIDsOfNames` был удален.  
  
## <a name="example"></a>Пример  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)