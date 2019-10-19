---
title: 'IActiveScript:: Жетскриптдиспатч | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575759"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Извлекает интерфейс `IDispatch` для методов и свойств, связанных с текущим выполняемым скриптом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrItemName`  
 окне Адрес буфера, содержащего имя элемента, для которого вызывающему объекту требуется связанный объект диспетчеризации. Если этот параметр имеет значение `NULL`, объект диспетчеризации содержит все глобальные методы и свойства, определенные сценарием, в качестве его членов. С помощью интерфейса `IDispatch` и связанного `ITypeInfo` интерфейса узел может вызывать методы скрипта или просматривать и изменять переменные скрипта.  
  
 `ppdisp`  
 заполняет Адрес переменной, которая получает указатель на объект, связанный с глобальными методами и свойствами скрипта. Если обработчик скриптов не поддерживает такой объект, возвращается `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
|`S_FALSE`|Обработчик скриптов не поддерживает объект диспетчеризации; параметр `ppdisp` имеет значение NULL.|  
  
## <a name="remarks"></a>Заметки  
 Поскольку методы и свойства могут быть добавлены путем вызова интерфейса [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , интерфейс `IDispatch`, возвращаемый этим методом, может динамически поддерживать новые методы и свойства. Аналогичным образом, метод `IDispatch::GetTypeInfo` должен возвращать новый уникальный интерфейс `ITypeInfo` при добавлении методов и свойств. Однако обратите внимание, что обработчики языков не должны изменять интерфейс `IDispatch` способом, который несовместим с предыдущим интерфейсом `ITypeInfo`. Это подразумевает, например, что идентификаторы DISPID никогда не будут использоваться повторно.  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)