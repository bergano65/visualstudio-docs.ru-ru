---
title: IActiveScriptError::GetSourceLineText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 702f1655b244116e1bb7dca3d5fc90de3d1f5bdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955010"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Извлекает строки в исходном файле, где произошла ошибка во время выполнения сценария обработчик сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Параметр  
 `pbstrSourceLine`  
 [out] Адрес буфера, который получает строки исходного кода, в которой произошла ошибка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если строки в исходном файле, который не был получен.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)