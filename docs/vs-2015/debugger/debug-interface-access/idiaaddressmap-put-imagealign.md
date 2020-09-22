---
title: IDiaAddressMap::p ut_imageAlign | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842668"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает выравнивание изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 неввал  
 окне Новое значение выравнивания изображения для исполняемого файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Образы (загруженные исполняемые файлы) согласовываются с указанными границами памяти. Это выравнивание может зависеть от текущей системной архитектуры и параметров компиляции и времени компоновки. Выравнивание изображения всегда находится в пределах диапазона байтов. Допустимы следующие значения выравнивания изображения: 1, 2, 4, 8, 16, 32 и 64 байты.  
  
 Текущее выравнивание изображения можно получить с помощью вызова метода [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
> Изображение уже загружено в момент, когда этот метод может быть вызван. `put_imageAlign`Метод обычно используется, когда изображение было перемещено или изменено, и требуется новое выравнивание.  
  
## <a name="see-also"></a>См. также:  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
