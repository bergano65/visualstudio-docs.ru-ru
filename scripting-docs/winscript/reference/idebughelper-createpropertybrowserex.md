---
title: IDebugHelper::CreatePropertyBrowserEx | Документация Майкрософт
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
ms.openlocfilehash: c3590fe05ef82f094dd5706f9f527b247d95eda8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097738"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Возвращает браузер свойств, который служит оболочкой VARIANT и позволяет выполнять пользовательские преобразование значениями VARIANT или типами VARTYPE в строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Имя корневой.  
  
 `pdat`  
 [in] Поток, выступающей в качестве свойства запроса. Если этот параметр имеет значение NULL, выполняется без упаковки.  
  
 `pdf`  
 [in] Объект, который предоставляет пользовательский формат для вариантов.  
  
 `ppdob`  
 [out] Браузер свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает браузер свойств, который служит оболочкой VARIANT и позволяет выполнять пользовательские преобразование значениями VARIANT или типами VARTYPE в строки.  
  
## <a name="see-also"></a>См. также  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Интерфейс IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)