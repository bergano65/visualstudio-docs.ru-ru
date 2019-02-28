---
title: IDiaSymbol::get_addressTaken | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c5ad583a29d38a61db6c485ad5adb3d33a4554f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615563"
---
# <a name="idiasymbolgetaddresstaken"></a>IDiaSymbol::get_addressTaken
Получает флаг, указывающий, ссылается ли другой символ на адрес этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressTaken ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если другой символ ссылается на этот адрес; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="example"></a>Пример
 В следующем примере `B` ссылки `A`. Таким образом, символ `A` `get_addressTaken` возвращает метод `TRUE`.

```C++
int A  = 0;
int* B = &A;
```

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)