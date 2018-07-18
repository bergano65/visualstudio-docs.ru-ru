---
title: IDiaInjectedSource::get_source | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8331086fff33f247ab030e3736e1e598c3af477d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459198"
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