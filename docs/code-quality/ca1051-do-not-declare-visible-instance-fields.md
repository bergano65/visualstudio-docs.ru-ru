---
title: CA1051. Не объявляйте видимые поля экземпляров
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 296e8cb4753d487573957de1108a8cb27778ef4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235792"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051. Не объявляйте видимые поля экземпляров

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип имеет поле экземпляра, не являющегося частным.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Поля главным образом следует использовать для данных реализации. Поля должны быть `private` или `internal` и должны предоставляться с помощью свойств. Очень просто получить доступ к свойству, так как оно обращается к полю, и код в функциях доступа свойства может измениться, так как функции типа расширяются без внесения критических изменений.

Свойства, которые просто возвращают значение закрытого или внутреннего поля, оптимизированы для выполнения по номиналу с доступом к полю; выигрыш в производительности от использования внешних видимых полей вместо свойств является минимальным. *Видимыми извне* называются `public`уровни `protected`доступности, `protected internal` ,`Public`и `Protected`(, `Protected Friend` и в Visual Basic).

Кроме того, открытые поля не могут быть защищены [запросами компоновки](/dotnet/framework/misc/link-demands). Дополнительные сведения см. в [разделе CA2112: Защищенные типы не должны предоставлять](../code-quality/ca2112-secured-types-should-not-expose-fields.md)поля. (Требования ссылок неприменимы к приложениям .NET Core.)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, сделайте поле `private` или `internal` предоставьте его с помощью свойства, видимого извне.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Подавить это предупреждение только в том случае, если известно, что пользователям требуется прямой доступ к полю. Для большинства приложений предоставляемые поля не обеспечивают производительность или преимущества сопровождения по сравнению со свойствами.

Пользователям может потребоваться доступ к полям в следующих ситуациях:

- в ASP.NET элементы управления содержимым веб-форм
- когда Целевая платформа использует `ref` для изменения полей, таких как платформы Model-View-ViewModel (MVVM) для WPF и UWP

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан тип (`BadPublicInstanceFields`), нарушающий это правило. `GoodPublicInstanceFields`Отображает исправленный код.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>См. также

- [Требования связывания](/dotnet/framework/misc/link-demands)
