---
title: IEnumRemoteDebugApplicationThreads::Reset | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Reset
ms.assetid: a6ad8a01-4cc0-4f9c-9cfe-c7448c753473
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a7c6fca01af5a3413ace6d95ca5c5879f4318ee
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154823"
---
# <a name="ienumremotedebugapplicationthreadsreset"></a>IEnumRemoteDebugApplicationThreads::Reset
Сбрасывает последовательность перечислений в начало.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод сбрасывает последовательность перечислений в начало.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)