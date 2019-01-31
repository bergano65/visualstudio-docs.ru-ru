---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f32b83ce4d44a18b3eb50d246a5d5ff4800316c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927637"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Позволяет клиенту включить или отключить вычисление и использование относительные виртуальные адреса (RVA).  
  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Адреса для отладки объектов, описанные по интерфейсов доступа к интерфейсу отладки, а также относительно исполняемого файла изображения базовый, могут быть получены как относительные виртуальные адреса.  
  
 Использование RVA включена в том случае, если сегменты изначально загружаются из PDB-файл. Чтобы получить текущее состояние использования RVA, вызовите [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) метод.  
  
 `put_relativeVirtualAddress` Метод должен вызываться для включения RVA после успешного вызова [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод устанавливает новый образ заголовки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)