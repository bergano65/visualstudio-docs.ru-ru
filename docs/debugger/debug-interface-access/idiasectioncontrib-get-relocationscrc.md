---
title: IDiaSectionContrib::get_relocationsCrc | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relocationsCrc method
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a57c46bef62039241c7d0cc064753199440893e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839515"
---
# <a name="idiasectioncontribgetrelocationscrc"></a>IDiaSectionContrib::get_relocationsCrc
Извлекает циклическую проверку избыточности (CRC) перемещения сведения для раздела.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_relocationsCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает контрольную СУММУ для области данных перемещение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)