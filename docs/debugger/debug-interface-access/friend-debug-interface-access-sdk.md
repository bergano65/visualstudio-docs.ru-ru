---
title: "Friend (SDK для доступа к интерфейсу отладки) | Microsoft Docs"
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
  - "дружественные функции [пакет SDK для доступа к интерфейсу отладки]"
  - "классы дружественных функций [пакет SDK для доступа к интерфейсу отладки]"
  - "Friend - символ"
ms.assetid: 5147a170-41ce-4727-8ace-c318e8d11647
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Friend (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Классы друга и дружественной функции определяются by `SymTagFriend` символы.  Их потомков родительских пользовательских типов \(udt\) и имеют a [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md) свойство.  
  
## Свойства  
 В следующей таблице показаны допустимые дополнительные свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Символ для родительского элемента определяемого пользователем типа.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|Идентификатор родительского класса символов.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Имя класса или функции.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagFriend` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для класса или функции.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
  
## См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)