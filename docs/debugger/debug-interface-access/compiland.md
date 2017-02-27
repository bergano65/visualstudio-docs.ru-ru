---
title: "Compiland | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "символ компилируемого объекта"
  - "компилируемые объекты, символ компилируемого объекта"
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Одно `SymTagCompiland` символ для каждого Compiland связанного с exe\-файла.  Данные разбиваются между символами с Compiland `SymTagCompiland` тег, который может быть восстановлена без загрузки дополнительных символов и символов с a compiland  `SymTagCompilandDetails` тег, может потребоваться загрузка дополнительных символов.  
  
## Свойства  
 В следующей таблице показаны свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE` если правка и кнопка продолжить были включены на компиляции.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для exe\-файла.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_libraryName](../Topic/IDiaSymbol::get_libraryName.md)|`BSTR`|Имя библиотеки или объектного файла, из которого был загружен объект.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Имя файла объектного файла compiland.|  
|[IDiaSymbol::get\_sourceFileName](../Topic/IDiaSymbol::get_sourceFileName.md)|`BSTR`|Имя исходного файла.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagCompiland` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
  
## См. также  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)