---
title: IDiaAddressMap::put_imageAlign | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6743d2a39f2326b167da746fbb2da928c0b75aaf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560771"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaAddressMap::put_imageAlign](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-put-imagealign).  
  
Задает выравнивание изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 NewVal  
 [in] Новое значение выравнивания изображения для исполняемого файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Изображения (загруженных исполняемых файлов) выравниваются по границы указанной области памяти. Такое выравнивание может влиять текущую архитектуру системы и параметрами времени компиляции и связывания. Выравнивание изображения всегда включен байтовым границам. Допустимы следующие значения выравнивания изображения: 1, 2, 4, 8, 16, 32 и 64 байта границы.  
  
 Текущий тип выравнивания изображения можно получить с помощью вызова [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) метод.  
  
> [!NOTE]
>  Когда этот метод может вызываться уже загрузки изображения. `put_imageAlign` Метод обычно используется, если изображение были перемещены и изменены, и новый выравнивание является обязательным.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)



