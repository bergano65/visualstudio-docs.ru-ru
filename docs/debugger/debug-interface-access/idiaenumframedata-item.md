---
title: "IDiaEnumFrameData::Item | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a33a0dad9f315f929a2ca0b032f8907f9567435b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Извлекает элемент кадра данных с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 индекс  
 [in] Индекс [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) извлекаемый объект. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) метод.  
  
 section  
 [out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) объект, представляющий элемент данных нужной рамки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)