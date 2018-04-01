---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cedf13b3d9c948835d54a4f294b610691c3ce8a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Возвращает компонент смещения начальный адрес диапазона локальных символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `offset`  
 [out] Возвращает часть смещения начальный адрес диапазона.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
> [!NOTE]
>  Возвращен код ошибки означает, что символ имеет сведения о динамической диапазоне.  
  
## <a name="remarks"></a>Примечания  
 Адрес, сформированный путем раздел и смещение — это начало диапазона, в котором символ является допустимой.  
  
 Чтобы получить раздел часть адреса, используйте [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)