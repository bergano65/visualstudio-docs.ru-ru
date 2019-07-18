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
ms.openlocfilehash: 037f629a205c7af24509b8ca2e409683d1f085ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546366"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401. Методы P/Invoke не должны быть видимыми

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут (также реализуется `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Описание правила
 Методы, помеченные атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute> атрибут (или методы, определенные с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) использовать службы вызова платформы для доступа к неуправляемому коду. Такие методы не следует делать видимыми. Сохраняя эти методы закрытым или внутренним, вы убедитесь, что библиотека не может использоваться для нарушения безопасности, позволяя вызывающим объектам доступ к неуправляемым API, которые в противном случае они не отвечает.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените уровень доступа для метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере объявляется метод, который нарушает это правило.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]