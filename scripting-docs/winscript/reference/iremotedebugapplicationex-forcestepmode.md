---
title: IRemoteDebugApplicationEx:ForceStepMode | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790858"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

Заставляет отладчик в пошаговом режиме.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>Параметры

`pStepThread`

[in] Поток для монитор отладки процесса к шагу. Если значение равно null, PDM очищает его пошагового выполнения потока.

## <a name="return-value"></a>Возвращаемое значение

Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.

|Значение|Описание:|
|-----------|-----------------|
|`S_OK`|Метод успешно выполнен.|

## <a name="see-also"></a>См. также

- [IRemoteDebugApplicationEx Interface](iremotedebugapplicationex-interface.md)