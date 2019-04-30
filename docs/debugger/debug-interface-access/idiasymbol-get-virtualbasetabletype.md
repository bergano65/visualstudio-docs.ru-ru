---
title: IDiaSymbol::get_virtualBaseTableType | Документация Майкрософт
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
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400885"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Извлекает тип указателя базовой виртуальной таблицы.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|`pRetVal`|[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , указывающий тип базовой таблицы.|

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Указатель базовой виртуальной таблицы (`vbtptr`) — это скрытый указатель в [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable, который обрабатывает наследование от виртуальных базовых классов. Объект `vbtptr` может иметь разные размеры в зависимости от наследуемые классы.

 Этот метод возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, который может использоваться для определения размера vbtptr.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)