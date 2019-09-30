---
title: CA1064. Исключения должны быть общими
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffc12d8d047be1bb13fcac133a61b047152ce3d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235321"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064. Исключения должны быть общими

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Исключение, не являющееся общим, наследуется <xref:System.Exception>непосредственно <xref:System.SystemException>от, <xref:System.ApplicationException>или.

## <a name="rule-description"></a>Описание правила
Внутреннее исключение видно только внутри собственной внутренней области. После выхода исключения за пределы внутренней области для перехвата исключения можно использовать только базовое исключение. Если внутренне исключение унаследовано от <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>, внешний код не будет иметь достаточно сведений, чтобы знать, что делать с исключением.

Но если в коде есть открытое исключение, которое позже используется в качестве основания для внутреннего исключения, разумно предположить, что код будет иметь возможность сделать что-то интеллектуальное с базовым исключением. Общее исключение будет содержать больше сведений <xref:System.Exception>, чем предоставлено, <xref:System.SystemException>или <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Сделайте исключение открытым или создайте производное внутреннее исключение из открытого исключения, которое не <xref:System.Exception>имеет значение, <xref:System.SystemException>или <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять сообщение из этого правила, если вы уверены во всех случаях, когда частное исключение будет перехвачено в собственной внутренней области.

## <a name="example"></a>Пример
Это правило срабатывает в первом примере метода Фирсткустомексцептион, поскольку класс Exception является производным непосредственно от Exception и является внутренним. Правило не срабатывает для класса Секондкустомексцептион, поскольку несмотря на то, что класс также является производным от Exception, класс объявлен как открытый. Третий класс также не запускает правило, так как он не является производным непосредственно от <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>или <xref:System.ApplicationException?displayProperty=fullName>.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
