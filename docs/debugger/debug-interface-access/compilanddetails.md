---
title: "CompilandDetails | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CompilandDetails - символ"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Данные разбиваются между символами с Compiland `SymTagCompiland` тег \(a\) и низкое сведения  `SymTagCompilandDetails` тег \(высокое сведения\).  `SymTagCompilandDetails` требуется при загрузке дополнительных символов.  Однако он предоставляет множество сведения о compiland, недоступно, a `SymTagCompiland` символ.  
  
## Свойства  
 В следующей таблице показаны свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|Конечный номер построения компилятора.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Конечный основной номер версии компилятора.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Конечный дополнительный номер версии компилятора.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Имя компилятора, который сформировал это compiland \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE` если правка и кнопка продолжить были включены на компиляции.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Номер построения начала компилятора.|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|Основной номер версии начала компилятора.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Дополнительный номер версии начала компилятора.|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|`TRUE` если это compiland имеет отладки сведения \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` если это compiland содержит управляемый код \(только в пакет SDK для доступа к интерфейсу отладки v8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` если compiland будет компилироваться с  [Параметр \/GS \(проверка безопасности буфера\)](/visual-cpp/build/reference/gs-buffer-security-check) переключатель компилятора \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` если compiland преобразован из общего кода промежуточного языка \(CIL\) в машинный код.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` если пользовательские типы \(udt\) были выровнены к некоторой указанной границы, то памяти \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|`TRUE` если compiland будет компилироваться с  [\/hotpatch \(Создать образ с обновлениями\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) переключатель компилятора \(только из пакета SDK для доступа к интерфейсу отладки v8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` если compiland будет компилироваться с  [Параметр \/LTCG \(создание кода во время компоновки\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) переключатель компилятора \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|Значение TRUE, если compiland, то модуль MSIL \(только из пакета SDK для доступа к интерфейсу отладки v8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|Язык исходного кода.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ, compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Платформы, на которой было компилироваться \(одно из compiland [Перечисление CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) значения\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagCompilandDetails` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
  
## Заметки  
 Компиляторы часто происходят в форму называемую двух траекторный компилятор; в некоторых версиях компилятора каждый этап обрабатываются отдельно программой.  Такие как начальное и конечное компиляторы, соответственно, следовательно, свойства символов для номеров версии конечной и начала.  
  
## См. также  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)