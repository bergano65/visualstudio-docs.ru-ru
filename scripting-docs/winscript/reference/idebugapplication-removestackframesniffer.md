---
title: IDebugApplication::RemoveStackFrameSniffer | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1462ff1382f3ccb844ccc98c6e6eec676a86c669
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159261"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Удаляет поставщик перечислитель кадра стека из этого приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCookie`  
 [in] Файл cookie, возвращенный `AddStackFrameSniffer` метод при добавлении поставщика перечислитель кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `RemoveStackFrameSniffer` Метод удаляет поставщик перечислитель кадра стека из этого приложения.  
  
## <a name="see-also"></a>См. также  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)