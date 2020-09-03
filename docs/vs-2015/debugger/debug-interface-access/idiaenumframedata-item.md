---
title: 'Идиаенумфрамедата:: Item | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0db365738e7c41c4a4e9f36b1942c5a64dedada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161264"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает элемент данных кадра с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 index  
 окне Индекс объекта [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) для извлечения. Индекс находится в диапазоне от 0 до `count` -1, где `count` возвращается методом [идиаенумфрамедата:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .  
  
 section  
 заполняет Возвращает объект [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий нужный элемент данных кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумфрамедата](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
