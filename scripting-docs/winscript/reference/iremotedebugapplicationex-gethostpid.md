---
title: IRemoteDebugApplicationEx:GetHostPid | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934587"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Возвращает идентификатор процесса для ведущего приложения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Параметры

`dwHostPid`

[out] Идентификатор процесса узла.

## <a name="return-value"></a>Возвращаемое значение

Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.

|Значение|Описание|
|-----------|-----------------|
|`S_OK`|Метод успешно выполнен.|

## <a name="remarks"></a>Примечания

Использовать в интегрированной среде разработки.

## <a name="see-also"></a>См. также

- [IRemoteDebugApplicationEx Interface](iremotedebugapplicationex-interface.md)