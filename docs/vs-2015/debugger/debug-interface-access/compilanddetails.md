---
title: CompilandDetails | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c385d82dfc9a4223610000642b82b8cffe4a7109
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561241"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CompilandDetails](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/compilanddetails).  
  
Сведения о единице компиляции разбивается между символами с `SymTagCompiland` тега (низкий деталей) и `SymTagCompilandDetails` тега (высокий уровень детализации). `SymTagCompilandDetails` требуется загрузка дополнительных символов. Тем не менее, он предоставляет широкий набор сведений о единице компиляции, который не входит в состав `SymTagCompiland` символов.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Номер сборки серверной части компилятора.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Серверной части основной номер версии компилятора.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Серверной части дополнительный номер версии компилятора.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Имя компилятора, которая является создателем этой единице компиляции (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Если изменить и продолжить была включена в компиляцию.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Номер построения интерфейса компилятора.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Интерфейсный основной номер версии компилятора.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Интерфейсный дополнительный номер версии компилятора.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Если этот единице компиляции отладочная информация (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Если этот единице компиляции содержит управляемый код (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Если был скомпилирован единице компиляции с помощью [/GS (проверка безопасности буфера)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) параметр компилятора (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Если в единице компиляции был преобразован из общих промежуточного языка (CIL) кода в машинный код.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Если определяемые пользователем типы (UDT), выровненным по некоторые указанные границы памяти (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Если был скомпилирован единице компиляции с помощью [/hotpatch (создать образ с обновлениями)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) параметр компилятора (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Если был скомпилирован единице компиляции с помощью [/LTCG (Создание кода во время компоновки)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) параметр компилятора (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Значение TRUE, если единице компиляции модуля промежуточного языка MSIL (Microsoft) (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Язык исходного кода.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ компилируемого объекта.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Платформы, на котором был скомпилирован единице компиляции (один из [перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) значения).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagCompilandDetails` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
  
## <a name="remarks"></a>Примечания  
 Компиляторы часто возвращаются в виде, называемая компилятором двухэтапный; в некоторых версиях компилятора для каждого обрабатывается отдельной программы. Они известны как компиляторы интерфейсной и серверной части, соответственно, поэтому свойства символа для внутреннего и внешнего интерфейса номера версии.  
  
## <a name="see-also"></a>См. также  
 [Компилируемого объекта](../../debugger/debug-interface-access/compiland.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



