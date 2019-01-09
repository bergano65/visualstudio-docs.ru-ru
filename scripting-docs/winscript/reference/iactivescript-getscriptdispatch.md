---
title: IActiveScript::GetScriptDispatch | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097686"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Извлекает `IDispatch` интерфейс для методов и свойств, связанных с текущего выполняемого сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrItemName`  
 [in] Адрес буфера, который содержит имя элемента, для которого вызывающей стороне требуется объект связанного диспетчеризации. Если этот параметр имеет `NULL`, содержит объект диспетчеризации в качестве его членов, все глобальные методы и свойства, определенные с помощью скрипта. Через `IDispatch` интерфейса и связанного `ITypeInfo` интерфейс, узел может вызвать методы сценариев или представление и изменения переменных сценария.  
  
 `ppdisp`  
 [out] Адрес переменной, которая получает указатель на объект, связанный с глобальные методы и свойства сценария. Если обработчик скриптов не поддерживает такой объект `NULL` возвращается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчеризации; `ppdisp` параметр имеет значение NULL.|  
  
## <a name="remarks"></a>Примечания  
 Так как методы и свойства можно добавить, вызвав метод [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) интерфейс, `IDispatch` интерфейс, возвращаемого этим методом динамически поддерживает новые методы и свойства. Аналогичным образом `IDispatch::GetTypeInfo` метод должен возвращать новый, уникальный `ITypeInfo` интерфейса при добавлении методов и свойств. Обратите внимание, что не должно меняться модулям языка `IDispatch` интерфейс в способом, несовместимые с любой предыдущей `ITypeInfo` возвращаемый интерфейс. К примеру, что идентификаторы DISPID никогда не будет использоваться повторно.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)