---
title: "IActiveScript::GetScriptDispatch | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Извлекает `IDispatch` интерфейс для методов и свойств, связанных с текущего выполняемого сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrItemName`  
 [in] Адрес буфера, который содержит имя элемента, для которого вызывающая сторона должна связанный объект. Если этот параметр равен `NULL`, содержит объект диспетчеризации членами все глобальные методы и свойства, определенные с помощью скрипта. Через `IDispatch` интерфейса и связанных `ITypeInfo` интерфейса узла можно вызвать методы скрипта или представление и изменения переменных сценария.  
  
 `ppdisp`  
 [out] Адрес переменной, которая получает указатель на объект, связанный с глобальные методы и свойства сценария. Если обработчик скриптов не поддерживает такой объект `NULL` возвращается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
|`S_FALSE`|Обработчик скриптов не поддерживает объекта распределения; `ppdisp` параметр имеет значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 Поскольку методы и свойства, можно добавлять путем вызова [iactivescriptparse —](../../winscript/reference/iactivescriptparse.md) интерфейс, `IDispatch` интерфейс, возвращаемый этим методом динамически поддерживает новые методы и свойства. Аналогичным образом `IDispatch::GetTypeInfo` метод должен возвращать новый, уникальный `ITypeInfo` интерфейс при добавлении методов и свойств. Обратите внимание, модули языка не должен изменяться `IDispatch` интерфейса в способом, который несовместим с любой предыдущей `ITypeInfo` возвращаемый интерфейс. Это подразумевает, например, что идентификаторы DISPID никогда не будет использоваться повторно.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)