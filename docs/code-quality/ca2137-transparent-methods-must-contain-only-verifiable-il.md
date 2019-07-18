---
title: CA2137. Прозрачные методы должны содержать только поддающийся проверке промежуточный язык
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f74b539d9382bf8b5f5fe319ff319cdf6f372340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806962"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137. Прозрачные методы должны содержать только поддающийся проверке промежуточный язык

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод содержит непроверяемый код или возвращает тип по ссылке.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает при попытках прозрачного кода безопасности выполнить непроверяемый MSIL. Однако это правило не содержит полную проверку IL, и вместо нее использует эвристику для выявления большинства нарушений проверки MSIL.

 Чтобы быть уверенным, что ваш код содержит только проверяемый код MSIL, запустите [Peverify.exe (средство PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) для сборки. Запустите PEVerify с **/ прозрачного** параметр, который ограничивает выходные данные только непроверяемый прозрачные методы которых приведет к ошибке. Если / прозрачного параметр не используется, PEVerify также проверяет критические методы, которые могут содержать непроверяемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибут, или удалите непроверяемый код.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В данном примере метод использует непроверяемый код и должны быть помечены <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]