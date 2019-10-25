---
title: IDiaSession::p ut_loadAddress | Документация Майкрософт
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
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741892"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Задает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Параметры
 `NewVal`

окне Загружается адрес исполняемого файла.

## <a name="remarks"></a>Заметки
 Свойства виртуального адреса символа (ва) вычисляются с помощью значения этого метода. Виртуальные адреса не вычисляются, если это свойство не имеет значение, отличное от нуля.

> [!NOTE]
> Этот метод следует вызывать при получении объекта [IDiaSession](../../debugger/debug-interface-access/idiasession.md) и перед началом использования объекта, если необходимо использовать виртуальные свойства в символах.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)