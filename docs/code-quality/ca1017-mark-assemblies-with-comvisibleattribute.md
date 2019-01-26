---
title: CA1017. Пометьте сборки с помощью ComVisibleAttribute
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 85c3abdce2845cc46e92ae6b0c4c9d565562bcad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959282"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017. Пометьте сборки с помощью ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибут, примененный к нему.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Атрибут определяет, как COM-клиентам доступ к управляемому коду. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM можно задать для всей сборки и затем переопределить ее для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки будет видимым COM-клиентам.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке. Если вы не хотите, чтобы сборка должна быть видимыми для COM-клиентам, примените атрибут и присвойте ему значение `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если требуется сборка должна быть видимой, примените атрибут и присвойте ему значение `true`.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут, примененный к запрещающий видимыми для COM-клиентам.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)