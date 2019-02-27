---
title: IDiaLoadCallback::NotifyOpenDBG | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97ca8b06a480d2fddb2002a0b9a19f878caa58f5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610727"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Вызывается, когда был открыт файл .dbg кандидатов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT NotifyOpenDBG ( 
   LPCOLESTR dbgPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Параметры
 `dbgPath`

[in] Полный путь файла .dbg.

 `resultCode`

[in] Код, который указывает на успешное завершение (`S_OK`) или Ошибка загрузки применительно к этому файлу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата, обычно учитывается.

## <a name="see-also"></a>См. также раздел
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)