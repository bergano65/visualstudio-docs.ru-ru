---
title: IDiaLoadCallback::NotifyOpenPDB | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5945ba54f1c09f4f13d2a982e90a3bb58cfb5f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839762"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Вызывается, когда кандидат PDB-файл открыт.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Параметры
 `pdbPath`

[in] Полный путь к PDB-файл.

 `resultCode`

[in] Код, который указывает на успешное завершение (`S_OK`) или Ошибка загрузки применительно к этому файлу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата, обычно учитывается.

## <a name="see-also"></a>См. также
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)