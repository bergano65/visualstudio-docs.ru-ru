---
title: 'Идебугхелпер:: Креатепропертибровсер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562497"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Возвращает обозреватель свойств, который упаковывает вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pvar`  
 окне Корневой вариант для просмотра.  
  
 `bstrName`  
 окне Имя, присваиваемое корневому каталогу.  
  
 `pdat`  
 окне Поток, в котором должны запрашиваться свойства. Если этот параметр имеет значение NULL, маршалинг не выполняется.  
  
 `ppdob`  
 заполняет Обозреватель свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает браузер свойств, который упаковывает вариант.  
  
## <a name="see-also"></a>См. также:  
 [Идебугхелпер:: креатепропертибровсерекс](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
   [интерфейса идебугхелпер](../../winscript/reference/idebughelper-interface.md)  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)