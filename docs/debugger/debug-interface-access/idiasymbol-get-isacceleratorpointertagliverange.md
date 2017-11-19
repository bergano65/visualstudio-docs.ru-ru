---
title: "IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2434dac0a4f0e4d9ff1c998f0cd70da4f9c558b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Возвращает флаг, указывающий, является ли символ соответствует *определения диапазона символов* для компонента тег в коде, скомпилированном для C++ AMP Accelerator переменной указателя. Символ определения диапазона является расположение переменной для диапазона адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Указатель на `BOOL` , указывающее, соответствует ли символ к символу Определение диапазона.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)