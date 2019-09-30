---
title: CA1401. Методы P/Invoke не должны быть видимыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d4a0a1c001407d947988497c422fdb8e88dd7c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234899"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401. Методы P/Invoke не должны быть видимыми

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Открытый или защищенный метод в открытом типе имеет <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут (также реализуется `Declare` с помощью ключевого слова [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]в).

## <a name="rule-description"></a>Описание правила
Методы, помеченные <xref:System.Runtime.InteropServices.DllImportAttribute> атрибутом (или методами, определенными с `Declare` помощью ключевого слова [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in), используют службы вызова платформы для доступа к неуправляемому коду. Такие методы не следует делать видимыми. Сохранив эти методы как частные или внутренние, вы убедитесь, что библиотека не может быть использована для нарушения безопасности, разрешая вызывающим объектам доступ к неуправляемым API, которые им не удалось вызвать в противном случае.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените уровень доступа метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере объявляется метод, нарушающий это правило.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]