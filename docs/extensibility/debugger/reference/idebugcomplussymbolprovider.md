---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugComPlusSymbolProvider"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет поставщика символов COM\+ с методами, которые относятся к управляемому коду.  
  
## Синтаксис  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## Примечания по реализации  
 Несмотря на то, что никакое разделение между интерфейсами, которые полезны в средство оценки выражений \(EE\) и те, которые предназначены для использования обработчиком отладки \(DE\), следующие методы будут, вероятно, процент DE разработчик только: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols и UpdateSymbols.  
  
## Методы  
 в дополнение к методам на [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|Указывает, загружаются символы отладки для указанного модуля заданный идентификатор домена приложения.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Создает тип из указанного примитивного типа.|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|Сопоставляет позиции документа в указанном модуле в массив адресов отладки.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Извлекает сведения о типе об указанном массиве заданной его адрес отладки.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Извлекает имя сборки с заданным модуль и домен приложения.|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|Извлекает классы с заданным атрибутом, которые реализованы в заданном языке программирования.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Извлекает классы с заданным атрибутом в данном модуле.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Извлекает точку входа приложения.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Извлекает адрес в пределах функции, представляющая заданное смещение линии.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Извлекает структуру локальных переменных для набора методов.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Возвращает имя, связанное с указанным токен заданной свой объект метаданных.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Извлекает символы отладки с заданным родительским атрибутом для заданного модуля.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Возвращает средство чтения символов для использования неуправляемого кода.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Возвращает тип символа заданного его адрес отладки.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Определяет, если указанная функция отладки удалена на адрес.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Определяет, если указанная функция считается устаревшей в отладочной адрес.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Указывает, скрыт код по указанному адресу.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Загружает указанные символы отладки в памяти.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Загрузить отладочные символы заданного потока данных.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Заменяет текущий символы отладки с этими в указанном потоке данных.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Выгружает символы отладки для указанного модуля из памяти.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Обновляет символы отладки в памяти с этими указанный поток данных.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll