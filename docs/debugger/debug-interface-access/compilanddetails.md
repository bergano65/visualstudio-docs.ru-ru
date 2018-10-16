---
title: CompilandDetails | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b1288a3bde1a8d17f40971744298adb1e1ecffb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468812"
---
# <a name="compilanddetails"></a>CompilandDetails
Сведения компилируемого объекта разбивается между символами с `SymTagCompiland` тег (низкий подробности) и `SymTagCompilandDetails` тег (высокий уровень детализации). `SymTagCompilandDetails` требуется загрузка дополнительных символов. Тем не менее, он предоставляет широкий набор сведений о компилируемого объекта, который недоступен с `SymTagCompiland` символов.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для этого типа символа.  
  
|Свойство.|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Номер построения серверной части компилятора.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Тыловой основной номер версии компилятора.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Тыловой дополнительный номер версии компилятора.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Имя компилятора, которое вызвало это компилируемого объекта (только в версии DIA SDK 8.0 или более поздней версии).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Если изменить и продолжить была включена в компиляцию.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Номер построения интерфейса компилятора.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Интерфейсный основной номер версии компилятора.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Интерфейсный дополнительный номер версии компилятора.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Если это компилируемого объекта имеет отладочной информации (только в версии DIA SDK 8.0 или более поздней версии).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Если это компилируемого объекта содержит управляемый код (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check) переключатель компилятора (только в версии DIA SDK 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Если компилируемого объекта было преобразовано из общих промежуточного языка (CIL) кода в машинный код.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Если определяемых пользователем типов (UDT), выровненный по указаны некоторые границы памяти (только в версии DIA SDK 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с [/hotpatch (создать образ с обновлениями)](/cpp/build/reference/hotpatch-create-hotpatchable-image) переключатель компилятора (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с [/LTCG (Создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation) переключатель компилятора (только в версии DIA SDK 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Значение TRUE, если компилируемого объекта является модулем промежуточного языка Майкрософт (MSIL) (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Язык исходного кода.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ компилируемого объекта.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Платформа, на которой была скомпилирована компилируемого объекта (один из [CV_CPU_TYPE_e-перечисление](../../debugger/debug-interface-access/cv-cpu-type-e.md) значения).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagCompilandDetails` (один из [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) значения).|  
  
## <a name="remarks"></a>Примечания  
 Компиляторы часто поставляются в форме, известной как компилятора двухпроходный; в некоторых версиях компилятора в каждом проходе обрабатывается отдельной программы. Эти функции известны как внешнего и внутреннего интерфейса компиляторы, соответственно, поэтому свойства символа номеров версий на внутреннем и внешнем.  
  
## <a name="see-also"></a>См. также  
 [Компилируемого объекта](../../debugger/debug-interface-access/compiland.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)