---
title: IDiaInjectedSource::get_crc | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39fb027c5e23d0d18443a22848b181e64347669a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598795"
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
Извлекает циклическую проверку избыточности (CRC) вычисляется на основе байты исходного кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_crc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает контрольную СУММУ, вычисленные из байты исходного кода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)