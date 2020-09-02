---
title: 'IDiaEnumDebugStreamData:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bdbf58321426890bffd45a08818dc5341bdfc3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187402"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число записей в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число извлекаемых записей.  
  
 cbData  
 окне Размер буфера данных в байтах.  
  
 пкбдата  
 заполняет Возвращает число возвращенных байтов. Если `data` параметр имеет значение null, то `pcbData` содержит общее число байтов данных, доступных для всех запрошенных записей.  
  
 data[]  
 заполняет Буфер, который должен быть заполнен данными записи отладочного потока.  
  
 pceltFetched  
 [вход, выход] Возвращает количество записей в `data` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если больше нет записей. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
