---
title: "IDiaAddressMap::set_addressMap | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49dc861b6c250c83a6c30e2dbd0fb5035671ff28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Предоставляет адрес сопоставляются поддерживают переводы макета изображения.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cbData`  
 [in] Число элементов в `data` параметра.  
  
 `data[]`  
 [in] Массив [структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) структуры, которые определяют схему преобразования.  
  
 `imagetoSymbols`  
 [in] `TRUE` Если `data` параметр определяет сопоставление из новый макет изображения для исходного макета (как описано в отладочных символов). `FALSE`Если `data` карта к макету записи образа из исходного макета.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Обычно пакет получает карты преобразования из PDB-файла программы. Если эти значения отсутствуют, [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод вызывается дважды: один раз с `imagetoSymbols` равным `TRUE` и один раз с `imagetoSymbols` равным `FALSE`. Преобразование адресов карты нельзя включить, используя [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) метод Если обе карты перевода.  
  
## <a name="see-also"></a>См. также  
 [Структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)