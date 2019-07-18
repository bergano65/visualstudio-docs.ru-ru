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
ms.openlocfilehash: 3e5f25887d8fdd5b5fb774cc2e8619c1a93432c1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442775"
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
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод позволяет модулю пользовательских скриптов для возврата статистики значимые пользовательского ведущего приложения.  
  
> [!NOTE]
> В настоящее время этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)