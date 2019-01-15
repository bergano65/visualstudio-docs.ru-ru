---
title: IDiaInjectedSource::get_crc | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3864cb92708f0b726ee73316fd2060c981f0a1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894984"
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
Извлекает циклическую проверку избыточности (CRC) вычисляется на основе байты исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает контрольную СУММУ, вычисленные из байты исходного кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)