---
title: 'Идиаенумфрамедата:: Фрамебива | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0560965858bd6d9ee823a6056332bdd9a7b654a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146501"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает кадр по виртуальному адресу (ва).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 виртуаладдресс  
 окне ВА, представляющая интерес к интересующему кадру.  
  
 frame  
 заполняет Возвращает объект [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий кадр, содержащий указанный адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если данные кадра не соответствуют указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумфрамедата](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
