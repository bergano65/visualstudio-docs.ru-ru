---
title: IRemoteDebugApplicationThreadEx:EnumGlobalContexts | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationThreadEx:EnumGlobalContexts
ms.assetid: a6c0bc3f-4afc-41e1-b734-06e252c5b171
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47fb195a2292f04c5dc2dd40ecdf94564a3b16bb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158270"
---
# <a name="iremotedebugapplicationthreadexenumglobalcontexts"></a>IRemoteDebugApplicationThreadEx:EnumGlobalContexts
Перечисляет контексты глобальное выражение для всех языков, работающих в этом потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Перечислитель, который перечисляет контексты глобальное выражение для всех языков, работающих в этом потоке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания