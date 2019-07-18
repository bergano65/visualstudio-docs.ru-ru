---
title: IDiaSession::put_loadAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01d004491feedff26c350cd7d40c544bc6b6de0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "64783748"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Задает адрес загрузки исполняемого файла, соответствующее к символам в данном хранилище символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Параметры
 `NewVal`

[in] Загрузить адрес для исполняемого файла.

## <a name="remarks"></a>Примечания
 Свойства символа виртуальный адрес (VA) вычисляются с помощью значения этого метода. Если это свойство не задано значение ненулевое, виртуальных адресов не вычисляются.

> [!NOTE]
> Этот метод необходимо вызвать при получении [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объекта и перед началом работы с помощью объекта, если необходимо использовать все виртуальные свойства на символы.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)