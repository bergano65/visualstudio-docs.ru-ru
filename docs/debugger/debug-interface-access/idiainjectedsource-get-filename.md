---
title: IDiaInjectedSource::get_filename | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26c68e4f58706fe9d65738e2e58b6ba011999e6a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619255"
---
# <a name="idiainjectedsourcegetfilename"></a>IDiaInjectedSource::get_filename
Получает имя файла для источника.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_filename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 pRetVal

[out] Возвращает имя файла для источника.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)