---
title: 'CA1064: исключения должны быть открытыми'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a47334da2879760142dd925917339a011890554
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547949"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: исключения должны быть открытыми
|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Исключение не являющиеся открытыми наследует непосредственно от <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.

## <a name="rule-description"></a>Описание правила
 Внутреннее исключение видна только внутри своей внутренней области. После выхода исключения за пределы внутренней области для перехвата исключения можно использовать только базовое исключение. Если внутренне исключение унаследовано от <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>, внешний код не будет иметь достаточно сведений, чтобы знать, что делать с исключением.

 Но если код содержит открытое исключение, которое затем используется как основа для внутреннего исключения, разумно предположить, что код, будут иметь возможность правильно обработать базовое исключение. Открытый исключение будет иметь больше информации, чем предлагает <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Сделать открытым исключение, или являются производными внутреннее исключение из общедоступного исключение, которое не является <xref:System.Exception>, <xref:System.SystemException>, или <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждения из этого правила, если имеется полная уверенность во всех случаях, что закрытый исключение будет перехвачено в рамках своей внутренней области.

## <a name="example"></a>Пример
 Это правило срабатывает в первом примере метода исключение FirstCustomException, так как класс исключений наследует непосредственно от Exception и является внутренним. Правило не срабатывают в классе SecondCustomException, так как несмотря на то, что этот класс также наследует непосредственно от Exception, класс объявлен как открытый. Третий класс также не срабатывает правило, так как он не является производным непосредственно <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, или <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
