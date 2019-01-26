---
title: CA2122. Не используйте косвенное представление методов с требованиями ссылки
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701b44b8018e7493305c5269a38908c454889b9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986154"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122. Не используйте косвенное представление методов с требованиями ссылки

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный член имеет [требования связывания](/dotnet/framework/misc/link-demands) и вызывается членом, который не выполняет каких-либо проверок безопасности.

## <a name="rule-description"></a>Описание правила
 Запрос компоновки проверяет разрешения только непосредственно вызывающего метода. Если член `X` делает требования безопасности не вызывали ее и вызывает код защищен требованием связывания, вызывающий объект без необходимых разрешений можно использовать `X` для доступа к защищенному члену.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Добавление безопасности [данные и моделирование](/dotnet/framework/data/index) или ссылка на элемент запросу, чтобы он больше не предоставляет незащищенный доступ к члену, защищенному запросом компоновки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно подавить предупреждение из этого правила, необходимо убедиться в том, что ваш код не предоставлял доступ к операциям или ресурсам, которые могут использоваться в злонамеренных целях.

## <a name="example-1"></a>Пример 1
 В следующих примерах это библиотека, которая нарушает правило и приложение, демонстрирующее слабость библиотеки. Пример библиотеки содержит два метода, которые вместе нарушают правило. `EnvironmentSetting` Метод защищен требованием связывания для неограниченного доступа к переменным среды. `DomainInformation` Метод выполняет требования безопасности, не вызывающих перед вызовом `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Пример 2
 Следующее приложение вызывает незащищенный член библиотеки.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

В этом примере выводятся следующие данные:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>См. также

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Требования связывания](/dotnet/framework/misc/link-demands)
- [Данные и моделирование](/dotnet/framework/data/index)