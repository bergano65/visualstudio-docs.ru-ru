---
title: "IDiaInjectedSource::get_crc | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34a3f5c0add8085556fd1e8e8efe6bdcaaac79ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
Извлекает циклическую проверку избыточности (CRC), вычисленный на основе байтов исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает контрольную СУММУ, вычисленный на основе байтов исходного кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)