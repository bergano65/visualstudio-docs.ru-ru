---
title: 'Идиаенумсимболс:: get__NewEnum | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::get__NewEnum method
ms.assetid: 879609ea-8e5a-4fa3-afa6-d24870fb4392
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dccfb37d2abe38a9fd1c805f03acd7172ca01af6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743960"
---
# <a name="idiaenumsymbolsget__newenum"></a>IDiaEnumSymbols::get__NewEnum
Возвращает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версию этого перечислителя.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Параметры
 претвал

заполняет Возвращает интерфейс `IUnknown`, представляющий <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версию этого перечислителя.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)