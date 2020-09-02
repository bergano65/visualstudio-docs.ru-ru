---
title: 'IDiaEnumDebugStreamData:: Skip | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e71d9631949fc9ae22f80b1b5be3b0662d918ddd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187363"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пропускает указанное число записей в перечислимой последовательности.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число записей для пропуска в последовательности перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение, `S_FALSE` Если больше нет записей для пропуска.  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
