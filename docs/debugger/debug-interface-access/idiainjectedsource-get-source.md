---
title: IDiaInjectedSource::get_source | Документация Майкрософт
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
ms.openlocfilehash: 2966405dfe3bb7e6134f5ef35e55b30ef6c66c6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909912"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Извлекает байты исходного кода.  
  
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
 [out] Возвращает число байтов, представляющий байты возвращенная. Если `data` — `NULL`, затем `pcbData` доступен общее число байтов данных.  
  
 `data[]`  
 [out] Буфер, который должен быть заполнен с помощью исходных байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)