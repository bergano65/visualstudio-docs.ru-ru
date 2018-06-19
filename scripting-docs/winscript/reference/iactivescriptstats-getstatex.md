---
title: IActiveScriptStats::GetStatEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725094"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Возвращает статистику пользовательского скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guid`  
 [in] Указывает, какой статистики для возврата. Семантика конкретных соответствует конкретным GUID является полностью определен обработчик.  
  
 `pluHi`  
 [out] Старшие 32 разряда 64-разрядное целое число без знака, представляющее статистику.  
  
 `pluLo`  
 [out] Младшие 32 разряда 64-разрядное целое число без знака, представляющее статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обеспечивает модуль пользовательский сценарий для получения статистики может применяться для пользовательского основного приложения.  
  
> [!NOTE]
>  В настоящее время этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)