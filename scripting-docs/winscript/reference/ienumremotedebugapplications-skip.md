---
title: IEnumRemoteDebugApplications::Skip | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Skip
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5ed991b02394e12f2e3e789b673149c9de18949
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159027"
---
# <a name="ienumremotedebugapplicationsskip"></a>IEnumRemoteDebugApplications::Skip
Пропускает заданное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество сегментов в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод пропускает указанное количество сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)