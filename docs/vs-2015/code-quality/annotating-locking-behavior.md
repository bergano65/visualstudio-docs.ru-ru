---
title: Annotating Locking Behavior | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: a5b34253485da233ba6e25841b6592068de6fb69
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295832"
---
# <a name="annotating-locking-behavior"></a>Аннотация поведения блокировки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во избежание ошибок параллелизма в многопоточных программах, всегда выполняйте соответствующую дисциплину блокировок и используйте заметки SAL.  
  
 Ошибки параллелизма, как известно, трудно воспроизвести, распознать и отладить в силу случайного характера их проявления. Рассуждение о последовательности потоков в лучшем случае представляется трудным и становится непрактичным при разработке основной части кода с более чем несколькими потоками. Поэтому рекомендуется следовать дисциплине блокировки в многопоточных программах. Например, проработка порядка блокировки при множественном захвате блокировок помогает избежать взаимоблокировок, а приобретение защитной блокировки до получения доступа к общему ресурсу помогает избежать состояния гонок.  
  
 К сожалению, простым на первый взгляд правилам блокировки удивительно сложно следовать на практике. A fundamental limitation in today’s programming languages and compilers is that they do not directly support the specification and analysis of concurrency requirements. Программисты должны полагаться на неофициальные комментарии к коду для выражения своих намерений о том, как они используют блокировки.  
  
 Заметки SAL параллелизма предназначены для помощи в определении побочных эффектов блокировки, ответственности за блокировку, владения данными, иерархии порядка блокировки и другого ожидаемого поведения блокировки. Выполняя неявные правила явно, заметки SAL параллелизма предоставляют последовательный способ для документирования того, как код использует правила блокировки. Заметки параллелизма также расширяют возможности средств анализа кода для поиска условий гонки, взаимоблокировки, несоответствующих операций синхронизации и других неявных ошибок параллелизма.  
  
## <a name="general-guidelines"></a>Общие рекомендации  
 Используя аннотации, вы можете формулировать договоры, которые неявно выражены определениями функций, между реализациями (вызываемыми объектами) и клиентами (вызывающими объектами), а также задавать инварианты и другие свойства программы, которые впоследствии могут повысить эффективность анализа.  
  
 SAL поддерживает множество различных типов примитивов блокирования, таких как критические секции, мьютексы, спин-блокировки и другие объекты ресурсов. Many concurrency annotations take a lock expression as a parameter. By convention, a lock is denoted by the path expression of the underlying lock object.  
  
 Некоторые правила учета владения потоком, которые следует помнить постоянно:  
  
- Спин-блокировки являются несчитающими блокировками, у которых есть определенный поток-владелец.  
  
- Мьютексы и критические секции являются считающими блокировками, у которых есть определенный поток-владелец.  
  
- Семафоры и события являются считающими блокировками, не имеющими определенного потока-владельца.  
  
## <a name="locking-annotations"></a>Locking Annotations  
 The following table lists the locking annotations.  
  
|Комментарий|Описание|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Добавляет заметки к функции и указывает, что функция после вызова увеличивает на единицу число монопольных блокировок объекта блокировок с именем `expr`.|  
|`_Acquires_lock_(expr)`|Аннотирует функцию и указывает, что функция после вызова увеличивает на единицу число блокировок объекта блокировок с именем `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Блокировка с именем `expr` получена.  Возникает ошибка, если блокировка уже захвачена.|  
|`_Acquires_shared_lock_(expr)`|Аннотирует функцию и указывает, что функция после вызова увеличивает на единицу число общих блокировок объекта блокировок с именем `expr`.|  
|`_Create_lock_level_(name)`|Оператор, который объявляет символ `name` символом уровня блокировки, благодаря чему он может быть использован в аннотациях `_Has_Lock_level_` и `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Annotates any object to refine the type information of a resource object. Sometimes a common type is used for different kinds of resources and the overloaded type is not sufficient to distinguish the semantic requirements among various resources. Ниже представлен список предварительно определенных параметров `kind`:<br /><br /> `_Lock_kind_mutex_`<br /> Lock kind ID for mutexes.<br /><br /> `_Lock_kind_event_`<br /> Lock kind ID for events.<br /><br /> `_Lock_kind_semaphore_`<br /> Lock kind ID for semaphores.<br /><br /> `_Lock_kind_spin_lock_`<br /> Lock kind ID for spin locks.<br /><br /> `_Lock_kind_critical_section_`<br /> Lock kind ID for critical sections.|  
|`_Has_lock_level_(name)`|Аннотирует объект блокировки и присваивает ему уровень блокировки `name`.|  
|`_Lock_level_order_(name1, name2)`|A statement that gives the lock ordering between `name1` and `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Аннотирует функцию и указывает, что в состоянии выполнения две блокировки, `expr1` и `expr2`, рассматриваются таким образом, как если бы они были одним и тем же объектом блокировки.|  
|`_Releases_exclusive_lock_(expr)`|Добавляет заметки к функции и указывает, что функция после вызова уменьшает на единицу число монопольных блокировок объекта блокировок с именем `expr`.|  
|`_Releases_lock_(expr)`|Аннотирует функцию и указывает, что функция после вызова уменьшает на единицу число блокировок объекта блокировок с именем `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Блокировка с именем `expr` снята. Возникает ошибка, если блокировка на данный момент не захвачена.|  
|`_Releases_shared_lock_(expr)`|Аннотирует функцию и указывает, что функция после вызова уменьшает на единицу число общих блокировок объекта блокировок с именем `expr`.|  
|`_Requires_lock_held_(expr)`|Аннотирует функцию и указывает, что перед вызовом функции количество блокировок объекта с именем `expr` не менее единицы.|  
|`_Requires_lock_not_held_(expr)`|Добавляет заметки к функции и указывает, что перед вызовом функции количество блокировок объекта с именем `expr` равно нулю.|  
|`_Requires_no_locks_held_`|Аннотирует функцию и указывает, что количество блокировок на всех объектах блокировки равно нулю.|  
|`_Requires_shared_lock_held_(expr)`|Аннотирует функцию и указывает, что перед вызовом функции количество общих блокировок объекта с именем `expr` не менее единицы.|  
|`_Requires_exclusive_lock_held_(expr)`|Добавляет заметки к функции и указывает, что перед вызовом функции количество монопольных блокировок объекта с именем `expr` не менее единицы.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Встроенные SAL для непредоставленных явно объектов блокировки  
 Certain lock objects are not exposed by the implementation of the associated locking functions.  В следующей таблице перечислены встроенные переменные SAL, которые содержат заметки для функций, действующих на эти защищенные объекты блокировки.  
  
|Комментарий|Описание|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Описывает отмену спин-блокировки.|  
|`_Global_critical_region_`|Описывает критическую область.|  
|`_Global_interlock_`|Описывает блокируемые операции.|  
|`_Global_priority_region_`|Описывает область приоритета.|  
  
## <a name="shared-data-access-annotations"></a>Shared Data Access Annotations  
 В следующей таблице перечисляются аннотации для доступа к разделяемым данным.  
  
|Комментарий|Описание|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Добавляет заметки к переменной и указывает на то, что при доступе к данной переменной количество блокировок объекта с именем `expr` не менее единицы.|  
|`_Interlocked_`|Annotates a variable and is equivalent to `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|The annotated function parameter is the target operand of one of the various Interlocked functions.  Those operands must have specific additional properties.|  
|`_Write_guarded_by_(expr)`|Добавляет заметки к переменной и указывает на то, что при изменении данной переменной количество блокировок объекта с именем `expr` не менее единицы.|  
  
## <a name="see-also"></a>См. также раздел  
 [Using SAL Annotations to Reduce C/C++ Code Defects](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Understanding SAL](../code-quality/understanding-sal.md)   
 [Annotating Function Parameters and Return Values](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotating Function Behavior](../code-quality/annotating-function-behavior.md)   
 [Annotating Structs and Classes](../code-quality/annotating-structs-and-classes.md)   
 [Specifying When and Where an Annotation Applies](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Intrinsic Functions](../code-quality/intrinsic-functions.md)   
 [Best Practices and Examples](../code-quality/best-practices-and-examples-sal.md)   
 [Code Analysis Team Blog](https://go.microsoft.com/fwlink/p/?LinkId=251197)
