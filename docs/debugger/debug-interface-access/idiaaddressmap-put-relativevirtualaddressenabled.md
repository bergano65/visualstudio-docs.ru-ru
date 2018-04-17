---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97dc30db5c11948c97359f7e2a888d78106a1996
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Позволяет клиенту включить или отключить расчет и использовать относительные виртуальные адреса (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 NewVal  
 [in] Значение `TRUE` для включения, или `FALSE` для отключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Адреса для отладки объектов, описанные DIA интерфейсами и относительно исполняемого образа базовый, могут быть получены как относительными виртуальными адресами.  
  
 Использование RVA включена, когда сегменты изначально загружаются из PDB-файла. Чтобы получить текущее состояние использование RVA, вызовите [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) метод.  
  
 `put_relativeVirtualAddress` Необходимо вызвать метод, чтобы включить RVA после успешного вызова [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод устанавливает новый образ заголовки.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)