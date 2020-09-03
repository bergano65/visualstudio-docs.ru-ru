---
title: 'IDiaAddressMap:: set_addressMap | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198653"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Предоставляет карту адресов для поддержки перевода макета изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cbData`  
 окне Число элементов в `data` параметре.  
  
 `data[]`  
 окне Массив структур [структуры диааддрессмапентри](../../debugger/debug-interface-access/diaaddressmapentry.md) , определяющий карту трансляции.  
  
 `imagetoSymbols`  
 [входные] `TRUE` значение, если `data` параметр определяет карту из нового макета изображения в исходный макет (как описано в разделе Отладочные символы). `FALSE` значение `data` , если является картой для нового макета изображения, полученного из исходного макета.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Обычно DIA извлекает карты преобразования адресов из файла базы данных программы (. pdb). Если эти значения отсутствуют, метод [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) вызывается дважды, один раз, если параметру присвоено `imagetoSymbols` значение `TRUE` и один раз, а `imagetoSymbols` параметру задано значение `FALSE` . Переводы сопоставления адресов нельзя включить с помощью метода [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , если не указаны оба сопоставления перевода.  
  
## <a name="see-also"></a>См. также:  
 [Структура Диааддрессмапентри](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
