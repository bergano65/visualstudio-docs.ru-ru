---
title: Класс иерархия символьных типов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8aeb208c4015d205efbfe018ee324a8ba0ede6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="class-hierarchy-of-symbol-types"></a>Иерархия классов символьных типов
В следующей таблице описаны символьных типов в иерархии классов.  
  
## <a name="symbol-types"></a>Типы символов  
  
|Тип символа|Описание|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Символ, используемый для представления каждого класса, структуры и объединения.|  
|[Enum (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Символ для перечислимых типов.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Символ для типов указателей.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Символ для массивов.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Символ для базовых типов|  
|[Typedef (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Символ, который представляет имена для других типов.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Символ, используемый для каждого базового класса определяемого пользователем типа (UDT).|  
|[Friend (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Символ friend классов и дружественные функции.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Символ для каждой уникальной функции подписи.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Символ для каждого параметра в функцию.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Символ для размера виртуальной таблицы.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Символ виртуальную таблицу.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Символ для типа поставщика.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Символ для типа, определенного в метаданных.|  
|[Измерение](../../debugger/debug-interface-access/dimension.md)|Символ для измерений массива.|  
  
> [!NOTE]
>  Каждый символ может иметь свойства, содержащие сведения о символов, а также ссылки на другие символы. Эти свойства перечислены в разделах отдельный символ.  
  
## <a name="see-also"></a>См. также  
 [Перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)