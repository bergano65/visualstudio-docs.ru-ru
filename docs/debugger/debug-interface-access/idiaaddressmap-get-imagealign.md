---
title: IDiaAddressMap::get_imageAlign | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c37d05025f6de870d6011e2abba31cd28f06f780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
Извлекает текущее выравнивание изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение выравнивания изображения из исполняемого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Образы выравниваются по границам памяти, в зависимости от того, как был загружен и создается образ. Выравнивание обычно находится на границы 1, 2, 4, 8, 16, 32 или 64 байта. Выравнивание изображения можно задать с помощью вызова [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)