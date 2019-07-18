---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283533b20614ea727be620669ea5ab66cf00e5ed
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62835778"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Возвращает число тегов указатель сочетаний клавиш в функции заглушки C++ AMP.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Параметры
 `count`

[out] Указатель на `DWORD` , содержащий количество сочетаний клавиш тегов указатель в C++ функции AMP заглушки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается на `IDiaSymbol` интерфейс, который соответствует функции заглушки accelerator C++ AMP.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)