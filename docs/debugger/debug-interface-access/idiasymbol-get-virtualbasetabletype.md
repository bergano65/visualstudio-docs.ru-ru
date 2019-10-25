---
title: 'IDiaSymbol:: get_virtualBaseTableType | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaddb8b71ba96511af3682b442c1e5c8e84a409c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738841"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Возвращает тип указателя виртуальной базовой таблицы.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|`pRetVal`|заполняет Возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , указывающий тип базовой таблицы.|

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Указатель виртуальной базовой таблицы (`vbtptr`) является скрытым указателем в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable, который обрабатывает наследование от виртуальных базовых классов. @No__t_0 может иметь разные размеры в зависимости от наследуемых классов.

 Этот метод возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , который можно использовать для определения размера вбтптр.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA v 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)