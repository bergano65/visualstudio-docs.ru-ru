---
title: 'Иактивескриптстатс:: Жетстатекс | Документация Майкрософт'
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
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576125"
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
 окне Указывает, какую статистику следует вернуть. Семантика, которая соответствует определенному идентификатору GUID, полностью определена подсистемой.  
  
 `pluHi`  
 заполняет Старшие 32 бит 64-разрядного целого числа без знака, представляющего статистику.  
  
 `pluLo`  
 заполняет Младший 32 бит 64-разрядного целого числа без знака, представляющего статистику.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод позволяет пользовательскому обработчику скриптов возвращать статистически значимые данные для пользовательского хоста.  
  
> [!NOTE]
> Этот метод в настоящее время не реализован.  
  
## <a name="see-also"></a>См. также  
 [Иактивескриптстатс:: stat](../../winscript/reference/iactivescriptstats-getstat.md)    
 [Интерфейс IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)