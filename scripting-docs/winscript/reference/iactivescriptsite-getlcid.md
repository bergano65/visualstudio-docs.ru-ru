---
title: IActiveScriptSite::GetLCID | Документация Майкрософт
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
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992766"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Возвращает идентификатор языкового стандарта, связанный с пользовательским интерфейсом главного приложения. Обработчик скриптов использует идентификатор, чтобы убедиться, что на соответствующем языке отображаются строки сообщений об ошибках и другие элементы пользовательского интерфейса, создаваемых обработчиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `plcid`  
 [out] Адрес переменной, которая получает идентификатор языкового стандарта для элементов пользовательского интерфейса, отображаемых обработчиком сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не реализован. Используйте системный языковой стандарт.|  
|`E_POINTER`|Указан недопустимый указатель.|  
  
## <a name="remarks"></a>Примечания  
 Если этот метод возвращает `E_NOTIMPL`, следует использовать системный код локали.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)