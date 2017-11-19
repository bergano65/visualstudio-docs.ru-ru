---
title: "CA1409: Видимые COM-типы должны быть создаваемыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8d9fe357142cf8b95be0298797c4a18e9ee0df7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: видимые COM-типы должны быть создаваемыми
|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Ссылочный тип, который специально помечен как видимый для модели объектов компонентов (COM) содержит открытый параметризованный конструктор, но не содержит открытого конструктора по умолчанию (без параметров).  
  
## <a name="rule-description"></a>Описание правила  
 Невозможно создать тип без открытого конструктора по умолчанию COM-клиентами. Однако тип можно по-прежнему осуществляться COM-клиентами Если доступен другим способом создания типа и передать его клиенту (например, через возвращаемое значение вызова метода).  
  
 Правило не учитывает типы, которые являются производными от <xref:System.Delegate?displayProperty=fullName>.  
  
 По умолчанию, являются видимыми для COM следующие: сборки, открытые типы, члены общих экземпляров в открытых типах и все элементы общих типов значений.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте открытый конструктор по умолчанию или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> из типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если предоставлены другие средства для создания и передачи объекта COM-клиент.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>См. также  
 [Уточнение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)