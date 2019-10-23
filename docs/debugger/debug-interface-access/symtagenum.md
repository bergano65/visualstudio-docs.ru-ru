---
title: Симтаженум | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738517"
---
# <a name="symtagenum"></a>SymTagEnum
Указывает тип символа.

## <a name="syntax"></a>Синтаксис

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Элементы
`SymTagNull` указывает, что символ не имеет типа.

`SymTagExe` указывает, что символ является EXE-файлом. Для хранилища символов существует только один символ `SymTagExe`. Он служит глобальной областью и не имеет лексического родителя.

`SymTagCompiland` указывает символ компилируемого объекта для каждого компонента компилируемого объекта хранилища символов. Для собственных приложений `SymTagCompiland` символы соответствуют объектным файлам, связанным с изображением. Для некоторых типов образов MSIL существует один компилируемого объекта для каждого класса.

`SymTagCompilandDetails` указывает, что символ содержит расширенные атрибуты компилируемого объекта. Для получения этих свойств может потребоваться загрузка компилируемого объекта символов.

`SymTagCompilandEnv` указывает, что символ — это строка среды, определенная для компилируемого объекта.

`SymTagFunction` указывает, что символ является функцией.

`SymTagBlock` указывает, что символ является вложенным блоком.

`SymTagData` указывает, что символ является данными.

`SymTagAnnotation` указывает, что символ относится к заметке кода. Дочерние элементы этого символа представляют собой постоянные строки данных (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Большинство клиентов игнорируют этот символ.

`SymTagLabel` указывает, что символ является меткой.

`SymTagPublicSymbol` указывает, что символ является открытым символом. Для собственных приложений этот символ является внешним символом COFF, обнаруженным при связывании изображения.

`SymTagUDT` указывает, что символ является определяемым пользователем типом (структурой, классом или объединением).

`SymTagEnum` указывает, что символ является перечислением.

`SymTagFunctionType` указывает, что символ является типом сигнатуры функции.

`SymTagPointerType` указывает, что символ является типом указателя.

`SymTagArrayType` указывает, что символ является типом массива.

`SymTagBaseType` указывает, что символ является базовым типом.

`SymTagTypedef` указывает, что символ является `typedef`, то есть псевдонимом для другого типа.

`SymTagBaseClass` указывает, что символ является базовым классом определяемого пользователем типа.

`SymTagFriend` указывает, что символ является дружественным для определяемого пользователем типа.

`SymTagFunctionArgType` указывает, что символ является аргументом функции.

`SymTagFuncDebugStart` указывает, что символ является конечным расположением кода пролога функции.

`SymTagFuncDebugEnd` указывает, что символ является начальным расположением кода эпилога функции.

`SymTagUsingNamespace` указывает, что символ является именем пространства имен, активным в текущей области.

`SymTagVTableShape` указывает, что символ является описанием виртуальной таблицы.

`SymTagVTable` указывает, что символ является указателем виртуальной таблицы.

`SymTagCustom` указывает, что символ является пользовательским символом и не интерпретируется DIA.

`SymTagThunk` указывает, что символ является преобразователем, используемым для обмена данными между 16 и 32 битным кодом.

`SymTagCustomType` указывает, что символ является пользовательским символом компилятора.

`SymTagManagedType` указывает, что символ находится в метаданных.

`SymTagDimension` указывает, что символ является многомерным массивом FORTRAN.

`SymTagCallSite` указывает, что символ представляет сайт вызова.

`SymTagInlineSite` указывает, что символ представляет встроенный веб-сайт.

`SymTagBaseInterface` указывает, что символ является базовым интерфейсом.

`SymTagVectorType` указывает, что символ является векторным типом.

`SymTagMatrixType` указывает, что символ является типом матрицы.

`SymTagHLSLType` указывает, что символ является типом языка шейдера высокого уровня.

## <a name="remarks"></a>Заметки
Все символы в файле отладки имеют идентифицирующий тег, указывающий тип символа.

Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

Значения в этом перечислении передаются следующим методам для ограничения области поиска конкретным типом символа:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
