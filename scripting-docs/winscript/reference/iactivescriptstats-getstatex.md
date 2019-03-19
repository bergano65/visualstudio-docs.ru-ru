---
title: IActiveScriptStats::GetStatEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5f1585e335fac0072eba48494bf8c27736a47f41
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149173"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Возвращает статистику пользовательского скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guid`  
 [in] Указывает, какой статистики для возврата. Семантика конкретных соответствует конкретному GUID является полностью определенные ядра.  
  
 `pluHi`  
 [out] Старшие 32 разряда 64-разрядного целого числа без знака, представляющее статистику.  
  
 `pluLo`  
 [out] Младшие 32 разряда 64-разрядного целого числа без знака, представляющее статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет модулю пользовательских скриптов для возврата статистики значимые пользовательского ведущего приложения.  
  
> [!NOTE]
>  В настоящее время этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)