---
title: IDiaAddressMap::set_imageHeaders | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51b68475b9ef0374f95febabc2997524bfd61259
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Задает изображения, заголовки, чтобы включить трансляцию относительный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 cbData  
 [in] Число байтов данных заголовка. Должно быть `n*sizeof(IMAGE_SECTION_HEADER)` где `n` число заголовков разделов в исполняемом файле.  
  
 данные]  
 [in] Массив `IMAGE_SECTION_HEADER` структур для использования в качестве заголовков изображения.  
  
 originalHeaders  
 [in] Значение `FALSE` с использованием нового образа, если заголовки изображения `TRUE` , если они отражают исходный образ перед обновлением. Как правило, это будет равен `TRUE` только в сочетании с вызовами [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `IMAGE_SECTION_HEADER` Структура объявляется в заголовке Winnt.h и представляет формат изображения раздел заголовок исполняемого файла.  
  
 Зависит от относительного виртуального адреса вычисления `IMAGE_SECTION_HEADER` значения. Обычно пакет получает из PDB-файл программы. Если эти значения отсутствуют, доступа к интерфейсу отладки не удается вычислить относительными виртуальными адресами и [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) возвращает `FALSE`. Клиент затем нужно вызвать [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) способ включения вычисления относительный виртуальный адрес после предоставления заголовков отсутствует изображение с само изображение.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)