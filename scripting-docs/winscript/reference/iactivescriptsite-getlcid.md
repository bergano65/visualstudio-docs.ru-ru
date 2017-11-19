---
title: "IActiveScriptSite::GetLCID | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Возвращает идентификатор языкового стандарта, связанный с пользовательским интерфейсом поставщика услуг размещения. Обработчик скриптов использует идентификатор для убедитесь, что строки сообщений об ошибках и других элементах пользовательского интерфейса, создаваемых обработчиком отображаются на соответствующем языке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `plcid`  
 [out] Адрес переменной, которая получает идентификатор языкового стандарта для элементов пользовательского интерфейса отображается обработчиком сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не реализован. Используйте стандарт определенная системой.|  
|`E_POINTER`|Указан недопустимый указатель.|  
  
## <a name="remarks"></a>Примечания  
 Если этот метод возвращает `E_NOTIMPL`, следует использовать идентификатор языкового стандарта, определенная системой.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)