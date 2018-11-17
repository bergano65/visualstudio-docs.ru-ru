---
title: IDiaAddressMap::put_imageAlign | Документация Майкрософт
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
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c745d6b9df5f58b4aa2431a051e6fa583c73d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773708"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



