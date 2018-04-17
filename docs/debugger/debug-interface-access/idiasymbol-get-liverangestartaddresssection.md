---
title: IDiaSymbol::get_liveRangeStartAddressSection | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d180cfe132897d39be3c9b27b4670ea0c927b208
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Возвращает раздел часть начальный адрес диапазона локальных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `section`  
 [out] Возвращает часть раздела начальный адрес диапазона.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
> [!NOTE]
>  Возвращен код ошибки означает, что символ имеет сведения о динамической диапазоне.  
  
## <a name="remarks"></a>Примечания  
 Адрес, сформированный путем раздел и смещение — это начало диапазона, в котором символ является допустимой.  
  
 Чтобы получить смещения часть адреса, используйте [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)