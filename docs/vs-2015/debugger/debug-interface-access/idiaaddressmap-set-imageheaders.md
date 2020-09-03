---
title: 'IDiaAddressMap:: set_imageHeaders | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198643"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает заголовки изображений для включения преобразования относительных виртуальных адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 cbData  
 окне Число байтов данных заголовка. Должно быть `n*sizeof(IMAGE_SECTION_HEADER)` `n` указано, где — число заголовков разделов в исполняемом файле.  
  
 data[]  
 окне Массив структур,  `IMAGE_SECTION_HEADER` используемых в качестве заголовков изображений.  
  
 оригиналхеадерс  
 окне Задайте значение, `FALSE` Если заголовки изображений относятся к новому образу, `TRUE` если они соответствуют исходному изображению до обновления. Как правило, это можно сделать `TRUE` только в сочетании с вызовами метода [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 `IMAGE_SECTION_HEADER`Структура объявляется в файле WINNT. h и представляет формат заголовка раздела Image исполняемого файла.  
  
 Относительные вычисления виртуальных адресов зависят от `IMAGE_SECTION_HEADER` значений. Обычно DIA извлекает эти данные из файла базы данных программы (. pdb). Если эти значения отсутствуют, DIA не может вычислить относительные виртуальные адреса и метод [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) возвращает `FALSE` . Затем клиент должен вызвать метод [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) , чтобы обеспечить относительный расчет виртуального адреса после предоставления отсутствующих заголовков изображений из самого образа.  
  
## <a name="see-also"></a>См. также:  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
