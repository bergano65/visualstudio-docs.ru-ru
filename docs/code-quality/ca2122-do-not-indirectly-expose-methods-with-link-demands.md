---
title: CA2122. Не используйте косвенное представление методов с требованиями ссылки
ms.date: 11/04/2016
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
ms.openlocfilehash: 340d8f0a45506f15cdd9281f7ecda463583c3144
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920829"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122. Не используйте косвенное представление методов с требованиями ссылки

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Открытый или защищенный член имеет [запросы компоновки](/dotnet/framework/misc/link-demands) и вызывается членом, который не выполняет проверки безопасности.

## <a name="rule-description"></a>Описание правила
Запрос компоновки проверяет разрешения только непосредственно вызывающего метода. Если член `X` не выполняет никаких требований к безопасности вызывающих объектов и вызывает код, защищенный запросом компоновки, вызывающий объект без необходимого разрешения может использовать `X` для доступа к защищенному члену.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Добавьте данные безопасности [и моделирование](/dotnet/framework/data/index) или требование к ссылке для члена, чтобы он больше не предохраняет незащищенный доступ к члену, защищенному с помощью запроса на подключение.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Чтобы безопасно отключить предупреждение из этого правила, необходимо убедиться, что код не предоставляет вызывающим объектам доступ к операциям или ресурсам, которые могут быть использованы необратимым образом.

## <a name="example-1"></a>Пример 1
В следующих примерах показана библиотека, нарушающая правило, и приложение, демонстрирующее слабость библиотеки. Пример библиотеки предоставляет два метода, которые вместе нарушают правило. `EnvironmentSetting` Метод защищен запросом компоновки для неограниченного доступа к переменным среды. Метод не выполняет никаких требований безопасности вызывающих объектов перед вызовом `EnvironmentSetting`. `DomainInformation`

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