---
title: 'Идиаенумсегментс:: get__NewEnum | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca94c078bb2b2598ffbe8e8098ac635cb698288
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744212"
---
# <a name="idiaenumsegmentsget__newenum"></a>IDiaEnumSegments::get__NewEnum
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
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)