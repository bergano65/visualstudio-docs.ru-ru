---
title: IDebugSyncOperation::InProgressAbort | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095528"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Отмена выполняемой операции в другом потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Операция не может быть отменена.|  
|`E_ABORT`|Не удалось выполнить операцию.|  
  
## <a name="remarks"></a>Примечания  
 Диспетчер отладки процессов вызывает этот метода в поток отладки, чтобы отменить операцию, которая выполняется в другом потоке.  
  
 Если `InProgressAbort` метод не может завершить операцию, он возвращает `E_ABORT` как можно скорее. Этот метод может возвращать `E_NOTIMPL` Если операция не может быть отменена.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)