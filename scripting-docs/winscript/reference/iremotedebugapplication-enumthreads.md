---
title: 'IRemoteDebugApplication:: EnumThreads | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumThreads
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ecc2da982e840e059e0d96d2b630190527d43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573851"
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
Перечисляет все потоки, связанные с приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pperdat`  
 заполняет Перечислитель, в котором перечислены все потоки, связанные с приложением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод перечисляет все потоки, связанные с приложением. Новые потоки могут быть добавлены в любое время.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)