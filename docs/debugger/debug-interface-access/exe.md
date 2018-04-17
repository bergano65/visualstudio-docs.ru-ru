---
title: Exe | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f6201aa125dd54cbd4f61f22e93d798957170d5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exe"></a>Exe
Exe — единственный символ отсутствует либо лексической или класса родителя, так как он представляет глобально файл .exe или .dll. Имеется только один символ с `SymTagExe` тег каждого файла. [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) метод возвращает символ.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для этого типа символа.  
  
|Свойство.|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Срок действия этого исполняемого файла.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` этого исполняемого файла.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` Если файл символов, связанные с этого исполняемого файла содержит типы C (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` Если закрытые символы были вырезаны из файла символа, связанного с этот исполняемый файл (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Значение, указывающее целевой Процессор (один из [CV_CPU_TYPE_e-перечисление](../../debugger/debug-interface-access/cv-cpu-type-e.md) значения).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Имя файла .exe.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Подписи исполняемого файла.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Полный путь к файлу PDB или DBG файл .exe.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagExe` (один из [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) значения).|  
  
## <a name="see-also"></a>См. также  
 [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)