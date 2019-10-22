---
title: 'Иактивескриптеррор:: Жетексцептионинфо | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f776a5f1a60b1280ab1f133ead04fb275782e5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576943"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Извлекает сведения об ошибке, которая произошла во время выполнения сценария обработчиком скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pexcepinfo`  
 заполняет Адрес структуры `EXCEPINFO`, которая получает сведения об ошибке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_FAIL`, если произошла ошибка.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)