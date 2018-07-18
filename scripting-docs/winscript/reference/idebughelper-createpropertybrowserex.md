---
title: IDebugHelper::CreatePropertyBrowserEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9bc219ea5c2ff9ff2860d36cd475985d825ae59
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727574"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Возвращает обозреватель свойств, который создает оболочку для типа VARIANT и обеспечивает пользовательские преобразования значений типа VARIANT или типов VARTYPE в строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvar`  
 [in] Корневой тип variant для просмотра.  
  
 `bstrName`  
 [in] Имя корневого.  
  
 `pdat`  
 [in] Потока, на котором будет запрашивать свойства. Если этот параметр имеет значение NULL, без упаковки не выполняется.  
  
 `pdf`  
 [in] Объект, который предоставляет пользовательский формат для вариантов.  
  
 `ppdob`  
 [out] Обозреватель свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает обозреватель свойств, который создает оболочку для типа VARIANT и обеспечивает пользовательские преобразования значений типа VARIANT или типов VARTYPE в строки.  
  
## <a name="see-also"></a>См. также  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Интерфейс IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)