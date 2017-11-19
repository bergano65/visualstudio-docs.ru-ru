---
title: "IDiaInjectedSource::get_source | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910b96d4114617957907ff1cd4eee4609ebaa250
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Извлекает байт исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cbData`  
 [in] Число байтов, представляющий размер буфера данных.  
  
 `pcbData`  
 [out] Возвращает число байтов, представляющий байты возвращается. Если `data` — `NULL`, затем `pcbData` доступен общее число байтов данных.  
  
 `data[]`  
 [out] Буфер, в котором должен быть заполнен с использованием исходных байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)