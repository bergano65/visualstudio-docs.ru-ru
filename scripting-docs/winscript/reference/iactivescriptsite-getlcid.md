---
title: 'IActiveScriptSite:: КОД_ЯЗЫКА | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570736"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Извлекает идентификатор локали, связанный с пользовательским интерфейсом узла. Обработчик скриптов использует идентификатор, чтобы убедиться, что строки ошибок и другие элементы пользовательского интерфейса, созданные ядром, отображаются на соответствующем языке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `plcid`  
 заполняет Адрес переменной, получающей код локали для элементов пользовательского интерфейса, отображаемых обработчиком скриптов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не реализован. Использовать языковой стандарт, определенный системой.|  
|`E_POINTER`|Указан недопустимый указатель.|  
  
## <a name="remarks"></a>Заметки  
 Если этот метод возвращает `E_NOTIMPL`, следует использовать определенный системой идентификатор языкового стандарта.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)