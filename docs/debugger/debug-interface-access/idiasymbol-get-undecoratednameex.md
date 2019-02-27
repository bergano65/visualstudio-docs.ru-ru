---
title: IDiaSymbol::get_undecoratedNameEx | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83fda196a50c433de182a64f39faef7a6ba6cb17
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607854"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Извлекает часть или вся недекорированное имя для C++ внутреннее имя (компоновка).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Параметры
 `undecoratedOptions`

[in] Включение управления, что возвращается сочетание флагов. См. в разделе "Примечания" конкретные значения, и что они делают.

 `pRetVal`

[out] Возвращает внешнее имя для C++ декорированное имя.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 `undecorateOptions` Может представлять собой сочетание следующих флагов.

> [!NOTE]
>  Помечать имена не определены в пакете SDK для доступа к интерфейсу отладки, поэтому вам нужно добавить объявления в код или использовать необработанные значения.

|Flag|Значение|Описание|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Включает полное undecoration.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Удаляет начальные символы подчеркивания от корпорации Майкрософт расширить ключевые слова.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Отключает расширения Microsoft расширенных ключевые слова.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Отключает расширения типа возвращаемого значения для основного объявления.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Отключает расширения модели объявления.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Отключает расширения языка спецификатора объявления.|
|UNDNAME_RESERVED1|0x0020|ЗАРЕЗЕРВИРОВАНО.|
|UNDNAME_RESERVED2|0x0040|ЗАРЕЗЕРВИРОВАНО.|
|UNDNAME_NO_THISTYPE|0x0060|Отключает все модификаторы на `this` типа.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Отключает расширения описатели доступа для участников.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Отключает расширения из throw — «сигнатур» для функций и указателей на функции.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Отключает расширения `static` или `virtual` членов.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Отключает расширения Microsoft модели для определяемого пользователем ТИПА возвращает.|
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates декорированные имена в 32-разрядной.|
|UNDNAME_NAME_ONLY|0x1000|Возвращает только имя для основного объявление; Возвращает только [области::] имя.  При развертывании шаблона params.|
|UNDNAME_TYPE_ONLY|0x2000|Входные данные — это просто тип кодирования; выполняет композицию абстрактный декларатор.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Доступны параметры реальных шаблона.|
|UNDNAME_NO_ECSU|0x8000|Подавляет enum/классом, структурой или объединением.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Отключает проверку для допустимых символах идентификаторов.|
|UNDNAME_NO_PTR64|0x20000|Не включает ptr64 в выходных данных.|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)