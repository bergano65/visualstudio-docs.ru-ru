---
title: IDiaAddressMap::set_imageHeaders | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3e2504030d3e8f28c1a41dea1c053c7e1deb1bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810244"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Наборы изображений заголовки, чтобы включить трансляцию относительный виртуальный адрес.  
  
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
 [in] Число байтов данных заголовка. Должно быть `n*sizeof(IMAGE_SECTION_HEADER)` где `n` число заголовков разделов в исполняемом файле.  
  
 данные]  
 [in] Массив `IMAGE_SECTION_HEADER` структур для использования в качестве заголовков образа.  
  
 originalHeaders  
 [in] Значение `FALSE` из нового образа, если заголовки изображение `TRUE` если они отражают исходное изображение до обновления. Как правило, это может быть присвоено `TRUE` только в сочетании с вызовами [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `IMAGE_SECTION_HEADER` Структура объявляется в файле Winnt.h и представляет формат изображения раздел заголовка исполняемого файла.  
  
 Относительный виртуальный адрес вычисления зависят от `IMAGE_SECTION_HEADER` значения. Как правило доступа к интерфейсу отладки извлекает их из PDB-файла программы. Если эти значения отсутствуют, доступа к интерфейсу отладки не сможет вычислить относительными виртуальными адресами и [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) возвращает метод `FALSE`. Клиент затем должен вызвать [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) способ включения вычисления относительного виртуального адреса после предоставления отсутствуют заголовки изображения из самого изображения.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



