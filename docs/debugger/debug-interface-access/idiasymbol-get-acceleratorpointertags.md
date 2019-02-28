---
title: IDiaSymbol::get_acceleratorPointerTags | Документация Майкрософт
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
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607958"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Возвращает все значения тега указатель сочетаний клавиш, которые соответствуют на функцию C++ AMP accelerator заглушки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Параметры
 `cnt`

[in] Размер выходного массива `pPointerTags`.

 `pcnt`

[out] Число тегов указатель сочетаний клавиш в функцию C++ AMP accelerator заглушки.

 `pPointerTags`

[out] Объект `DWORD` указатель на массив, заполненный со значениями тегов accelerator указателя в функцию C++ AMP accelerator заглушки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается на `IDiaSymbol` интерфейс, который соответствует функции заглушки accelerator C++ AMP.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)