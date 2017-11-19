---
title: "IDiaAddressMap::put_imageAlign | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38856520641ff2ea191e3f712a1f355e841e1aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Задает выравнивание изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 NewVal  
 [in] Новое значение выравнивания изображения для исполняемого файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Изображения (загруженных исполняемых файлов) выравниваются по заданной памяти границы. Выравнивание, это может повлиять текущую архитектуру системы и параметров времени компиляции и связывания. Выравнивание изображения всегда является в байт. Допустимы следующие значения выравнивания для изображений: 1, 2, 4, 8, 16, 32 и 64 байта границы.  
  
 Текущее выравнивание изображения можно получить с помощью вызова [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) метод.  
  
> [!NOTE]
>  В момент вызова этого метода уже загружено изображение. `put_imageAlign` Метод обычно используется, когда изображение перемещены или изменены, и новый выравнивание является обязательным.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)