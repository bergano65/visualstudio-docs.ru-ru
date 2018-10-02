---
title: FunctionType | Документация Майкрософт
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
- function signature
- FunctionType symbol
ms.assetid: 646a07e7-9d4f-4e21-95e3-3e403cdd4843
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4df43e751a07e9116f442a04c1fd934792c24504
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573401"
---
# <a name="functiontype"></a>FunctionType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [FunctionType](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/functiontype).  
  
Каждой подписи unique-функция определяется `SymTagFunctionType` символов. Каждый параметр определяется как символ дочерний класс с `SymTagFunctionArgType` тега.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены дополнительные допустимые свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|`DWORD`|Одно из значений из [перечисление CV_call_e](../../debugger/debug-interface-access/cv-call-e.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Класс, что этой функции (или метод) является членом.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Идентификатор символа родительского класса.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Если функция отмечена как константа.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Число параметров функции.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего единице компиляции.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|`IDiaSymbol*`|Тип метода указатель на объект («this»).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagFunctionType` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`LONG`|Логическое «this» корректором для метода.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для типа возвращаемого значения.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Если функция не выровнен.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Если функция отмечена как переменное.|  
  
## <a name="see-also"></a>См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)



