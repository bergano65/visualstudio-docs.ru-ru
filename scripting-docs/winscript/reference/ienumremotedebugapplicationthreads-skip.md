---
title: 'Иенумремотедебугаппликатионсреадс:: Skip | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Skip
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Skip
ms.assetid: bb13a18b-bcf8-4542-8b1a-55a4f2769536
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92a92c53b4f7638893a5f5a73810e9b939c725b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577776"
---
# <a name="ienumremotedebugapplicationthreadsskip"></a>IEnumRemoteDebugApplicationThreads::Skip
Пропускает указанное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 окне Количество сегментов в последовательности перечисления, которые необходимо пропустить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод пропускает указанное число сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)