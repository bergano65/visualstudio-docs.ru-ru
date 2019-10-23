---
title: Компиланддетаилс | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745421"
---
# <a name="compilanddetails"></a>CompilandDetails
Сведения компилируемого объекта разбиваются между символами с помощью тега `SymTagCompiland` (с низким уровнем детализации) и тега `SymTagCompilandDetails` (с подробными сведениями). `SymTagCompilandDetails` требуется загрузка дополнительных символов. Однако он предоставляет обширную информацию о компилируемого объекта, которая недоступна для `SymTagCompiland`ного символа.

## <a name="properties"></a>Свойства
 В следующей таблице показаны свойства, которые являются допустимыми для этого типа символов.

|свойство;|Тип данных|Описание|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Номер внутренней сборки компилятора.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Основной номер версии компилятора.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Дополнительный номер версии компилятора.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Имя компилятора, который создал этот компилируемого объекта (только в пакете SDK DIA версии 8.0 или более поздней).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`, если была включена возможность "изменить и продолжить" во время компиляции.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Номер сборки внешнего интерфейса компилятора.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Основной номер версии компилятора внешнего интерфейса.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Дополнительный номер версии компилятора для внешнего интерфейса.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE`, содержит ли компилируемого объекта сведения об отладке (только в пакете SDK DIA версии 8.0 или более поздней).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`, если этот компилируемого объекта содержит управляемый код (только в пакете SDK DIA версии 8.0 или более поздней).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`, если компилируемого объекта был скомпилирован с параметром компилятора [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check) (только в DIA SDK v 8.0 или более поздней версии).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`, если компилируемого объекта был преобразован из кода на основе стандартного промежуточного языка (CIL) в машинный код.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`, если определяемые пользователем типы (UDT) были согласованы с определенной границей памяти (только в пакете SDK версии 8.0 или более поздних версиях) DIA.|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE`, если компилируемого объекта был скомпилирован с параметром компилятора [/hotpatch (Create допускающего оперативное обновление Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (только в пакете SDK для Dia версии 8.0 или более поздней).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`, если компилируемого объекта был скомпилирован с параметром компилятора [/LTCG (создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation) (только в пакете SDK Dia версии 8.0 или более поздней).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Значение TRUE, если компилируемого объекта является модулем MSIL (только в пакете SDK DIA версии 8.0 или более поздней).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Язык исходного кода.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для компилируемого объекта.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексического родителя символа.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Платформа, на которой была скомпилирована компилируемого объекта (одно из значений [перечисления CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagCompilandDetails` (одно из значений [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Заметки
 Компиляторы часто бывают в форме, известной как двухэтапный компилятор. в некоторых версиях компилятора каждый проход обрабатывается отдельной программой. Они называются внутренними и внутренними компиляторами, соответственно, свойствами символов для номеров серверной и клиентской версий.

## <a name="see-also"></a>См. также
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)