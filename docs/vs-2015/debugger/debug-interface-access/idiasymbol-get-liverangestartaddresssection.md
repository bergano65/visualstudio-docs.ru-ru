---
title: IDiaSymbol::get_liveRangeStartAddressSection | Документация Майкрософт
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
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49985c1ca0ddb1b20a3b498a3dadba45b58e6c0b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563099"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_liveRangeStartAddressSection](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection).  
  
Возвращает часть раздела начальный адрес диапазона, в котором локальный символ является допустимой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `section`  
 [out] Возвращает компонент разделе начальный адрес диапазона.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Возвращен код ошибки означает, что символ не имеет сведения о динамической диапазона.  
  
## <a name="remarks"></a>Примечания  
 Адрес, образованное раздела и смещение — это начало диапазона, в котором символ является допустимой.  
  
 Чтобы получить смещения часть адреса, используйте [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



