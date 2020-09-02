---
title: Компиланддетаилс | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703003"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Сведения компилируемого объекта разбиваются между символами с помощью `SymTagCompiland` тега (с низким уровнем детализации) и `SymTagCompilandDetails` тега (с подробными сведениями). `SymTagCompilandDetails` требуется загрузка дополнительных символов. Однако он предоставляет обширную информацию о компилируемого объекта, которая недоступна для `SymTagCompiland` символа.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице показаны свойства, которые являются допустимыми для этого типа символов.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Номер внутренней сборки компилятора.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Основной номер версии компилятора.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Дополнительный номер версии компилятора.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Имя компилятора, который создал этот компилируемого объекта (только в пакете SDK DIA версии 8.0 или более поздней).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Если была включена возможность "изменить и продолжить" во время компиляции.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Номер сборки внешнего интерфейса компилятора.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Основной номер версии компилятора внешнего интерфейса.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Дополнительный номер версии компилятора для внешнего интерфейса.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Если у компилируемого объекта есть отладочная информация (только в пакете SDK DIA версии 8.0 или более поздней).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Если этот компилируемого объекта содержит управляемый код (только в пакете SDK DIA версии 8.0 или более поздней).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с параметром компилятора [/GS (проверка безопасности буфера)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) (только в пакете SDK Dia версии 8.0 или более поздней).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Если компилируемого объекта был преобразован из кода на основе общего промежуточного языка (CIL) в машинный код.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Если определяемые пользователем типы (UDT) были согласованы с определенной границей памяти (только в DIA SDK версии 8.0 или более поздней).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с параметром компилятора [/hotpatch (Create допускающего оперативное обновление Image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) (только в пакете SDK для Dia версии 8.0 или более поздней).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Если компилируемого объекта был скомпилирован с параметром компилятора [/LTCG (создание кода во время компоновки)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) (только в пакете SDK Dia версии 8.0 или более поздней).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Значение TRUE, если компилируемого объекта является модулем MSIL (только в пакете SDK DIA версии 8.0 или более поздней).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Язык исходного кода.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для компилируемого объекта.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексического родителя символа.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Платформа, на которой была скомпилирована компилируемого объекта (одно из значений [перечисления CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagCompilandDetails` (одно из значений [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) ).|  
  
## <a name="remarks"></a>Remarks  
 Компиляторы часто бывают в форме, известной как двухэтапный компилятор. в некоторых версиях компилятора каждый проход обрабатывается отдельной программой. Они называются внутренними и внутренними компиляторами, соответственно, свойствами символов для номеров серверной и клиентской версий.  
  
## <a name="see-also"></a>См. также:  
 [Компилируемого объекта](../../debugger/debug-interface-access/compiland.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
