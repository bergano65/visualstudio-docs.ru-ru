---
title: IDiaImageData::get_relativeVirtualAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_relativeVirtualAddress method
ms.assetid: e6d6deee-dc12-4b38-af15-f917b2d4368e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a53dc7d890f76af562faf3f585914423b3d4fd94
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925647"
---
# <a name="idiaimagedatagetrelativevirtualaddress"></a>IDiaImageData::get_relativeVirtualAddress
Извлекает расположение виртуальной памяти модуля относительно приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает смещение относительного виртуальной памяти модуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)