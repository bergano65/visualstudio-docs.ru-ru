---
title: CA1017. Пометьте сборки с помощью ComVisibleAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 073332738a01cb299b2b185c6fca20131222f981
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236257"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017. Пометьте сборки с помощью ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
К сборке не <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> применен атрибут.

## <a name="rule-description"></a>Описание правила
Атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> определяет, как клиенты COM обращаются к управляемому коду. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM может быть задана для всей сборки, а затем переопределена для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки становится видимым для клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, добавьте атрибут в сборку. Если вы не хотите, чтобы сборка была видима клиентам COM, примените атрибут и задайте для `false`него значение.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Если необходимо, чтобы сборка была видимой, примените атрибут и задайте для `true`него значение.

## <a name="example"></a>Пример
В следующем примере показана сборка с <xref:System.Runtime.InteropServices.ComVisibleAttribute> примененным атрибутом, чтобы предотвратить ее видимость для COM-клиентов.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)