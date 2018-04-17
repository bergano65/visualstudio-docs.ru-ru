---
title: 'CA1409: Видимые COM-типы должны быть создаваемыми | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8ddd3d9a1a239f19758f1bdb9ab289bee3a8f6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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