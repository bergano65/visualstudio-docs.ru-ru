---
title: 'CA1064: исключения должны быть открытыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5e704793aeef211ccabd4f2c9993834af205a14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663627"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: исключения должны быть открытыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Исключение, не являющееся общим, наследуется непосредственно от <xref:System.Exception>, <xref:System.SystemException> или <xref:System.ApplicationException>.

## <a name="rule-description"></a>Описание правила
 Внутреннее исключение видно только внутри собственной внутренней области. После выхода исключения за пределы внутренней области для перехвата исключения можно использовать только базовое исключение. Если внутреннее исключение наследуется от <xref:System.Exception>, <xref:System.SystemException> или <xref:System.ApplicationException>, внешний код не будет иметь достаточных сведений, чтобы узнать, что делать с этим исключением.

 Но если в коде есть открытое исключение, которое позже используется в качестве основания для внутреннего исключения, разумно предположить, что код будет иметь возможность сделать что-то интеллектуальное с базовым исключением. Общее исключение будет содержать больше информации, чем предоставлено в T:System.Exception, Т:систем.системексцептион или Т:систем.аппликатионексцептион.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Сделайте исключение общедоступным или создайте производное от него внутреннее исключение, которое не <xref:System.Exception>, <xref:System.SystemException> или <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять сообщение из этого правила, если вы уверены во всех случаях, когда частное исключение будет перехвачено в собственной внутренней области.

## <a name="example"></a>Пример
 Это правило срабатывает в первом примере метода Фирсткустомексцептион, поскольку класс Exception является производным непосредственно от Exception и является внутренним. Правило не срабатывает для класса Секондкустомексцептион, поскольку несмотря на то, что класс также является производным от Exception, класс объявлен как открытый. Третий класс также не запускает правило, так как он не является производным непосредственно от <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> или <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
