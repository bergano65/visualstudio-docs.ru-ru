---
title: 'Идебугхелпер:: Креатепропертибровсерекс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576499"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Возвращает обозреватель свойств, который упаковывает вариант и позволяет выполнить пользовательское преобразование значений типа VARIANT или типа VARTYPE в строки.  
  
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
 окне Корневой вариант для просмотра.  
  
 `bstrName`  
 окне Имя, присваиваемое корневому каталогу.  
  
 `pdat`  
 окне Поток, в котором должны запрашиваться свойства. Если этот параметр имеет значение NULL, маршалинг не выполняется.  
  
 `pdf`  
 окне Объект, предоставляющий пользовательское форматирование для вариантов.  
  
 `ppdob`  
 заполняет Обозреватель свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает браузер свойств, который создает оболочку для VARIANT и позволяет выполнить пользовательское преобразование значений типа VARIANT или типа VARTYPE в строки.  
  
## <a name="see-also"></a>См. также:  
 [Идебугхелпер:: креатепропертибровсер](../../winscript/reference/idebughelper-createpropertybrowser.md)   
   [интерфейса идебугхелпер](../../winscript/reference/idebughelper-interface.md)  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)