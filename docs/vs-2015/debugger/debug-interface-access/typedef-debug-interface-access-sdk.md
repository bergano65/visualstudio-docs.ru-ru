---
title: Определение типа (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Typedef symbol [DIA SDK]
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2514aab11008dcc1651dff46b84cec4f4a5a8f12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990535"
---
# <a name="typedef-debug-interface-access-sdk"></a>Typedef (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Символы с `SymTagTypedef` теги вводят имена для других типов.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены дополнительные допустимые свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Один из [перечисление BasicType](../../debugger/debug-interface-access/basictype.md) значения.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Родительский класс это определение типа, если таковые имеются.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Идентификатор символа родительского класса.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` Если это определение типа имеет конструктор.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Если это определение типа помечается как константа.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` Если это определение типа имеет оператор присваивания.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` Если это определение типа есть оператор приведения.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` Если это определение типа имеет вложенные типы.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Длина это определение типа в байтах.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего единице компиляции.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Имя определения типа (typedef).|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` Если это определение типа является вложенным в лексической области действия.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` Если это определение типа имеет перегруженного оператора.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` Если это определение типа упаковывается.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|`TRUE` Если это определение типа является ссылкой.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` Если это определение типа в неглобальные лексической области видимости.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagTypedef` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для базового типа.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Один из [перечисление UdtKind](../../debugger/debug-interface-access/udtkind.md) значения.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Если это определение типа не выровнен.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Символ, который описывает форму виртуальной таблицы.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Идентификатор символа фигуры виртуальной таблицы.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Если это определение типа помечается как переменное.|  
  
## <a name="remarks"></a>Примечания  
 Так как определение типа может представлять класс, указатель или определяемого пользователем типа (UDT), символ для typedef совместно использует те же свойства, как один из этих типов, символов.  
  
## <a name="see-also"></a>См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
