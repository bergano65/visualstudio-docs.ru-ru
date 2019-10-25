---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741117"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Возвращает все значения тегов указателя ускорителя, соответствующие функции- C++ заглушке ускорителя amp.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Параметры
 `cnt`

окне Размер `pPointerTags` массива вывода.

 `pcnt`

заполняет Число тегов указателей ускорителя в функции- C++ заглушке ускорителя amp.

 `pPointerTags`

заполняет Указатель массива `DWORD`, который заполняется значениями тега указателя-ускорителя в функции заглушки ускорителя C++ amp.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод вызывается для интерфейса `IDiaSymbol`, соответствующего функции- C++ заглушке ускорителя amp.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)