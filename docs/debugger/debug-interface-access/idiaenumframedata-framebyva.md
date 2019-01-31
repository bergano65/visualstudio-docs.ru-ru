---
title: IDiaEnumFrameData::frameByVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5c6f6252c23069ffce01b9b790a44b24efbd80a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949380"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Возвращает кадр, виртуальный адрес (VA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 virtualAddress  
 [in] VA кадра интерес.  
  
 фрейм  
 [out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий рамку, содержащую указанный адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если нет кадров данных, соответствующей указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)