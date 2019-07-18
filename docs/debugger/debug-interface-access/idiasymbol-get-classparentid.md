---
title: IDiaSymbol::get_classParentId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParentId method
ms.assetid: f11e3ccb-215d-418c-b8c3-e63159234915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70b6b49ab8a493102d10c03291a326ae0d23a747
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64800476"
---
# <a name="idiasymbolgetclassparentid"></a>IDiaSymbol::get_classParentId
Получает идентификатор родительского класса символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_classParentId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает идентификатор родительского класса символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Идентификатор — это уникальное значение, созданные с помощью пакета SDK доступа к интерфейсу отладки, чтобы пометить все символы как уникальный.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)