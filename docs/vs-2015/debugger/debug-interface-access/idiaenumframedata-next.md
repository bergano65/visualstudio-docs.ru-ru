---
title: 'Идиаенумфрамедата:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe8735511e9830542ce8622a6d984a0a817671
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161218"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число элементов данных кадра в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Количество элементов данных кадра в перечислителе для извлечения.  
  
 rgelt  
 заполняет Массив объектов [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , которые должны быть заполнены элементами данных запрошенного кадра.  
  
 pceltFetched  
 заполняет Возвращает количество элементов данных кадра в выбранном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если больше нет записей. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумфрамедата](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
