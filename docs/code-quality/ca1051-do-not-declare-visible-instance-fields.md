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
ms.openlocfilehash: c5dd8a4b2d0b32a8c52f75dee6fd765a7ea6ec9a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547555"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051. Не объявляйте видимые поля экземпляров

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип имеет поле экземпляра, не являющегося частным.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Поля главным образом следует использовать для данных реализации. Поля должны быть `private` или `internal` и должны предоставляться с помощью свойств. Очень просто получить доступ к свойству, так как оно обращается к полю, и код в функциях доступа свойства может измениться, так как функции типа расширяются без внесения критических изменений. Свойства, которые просто возвращают значение закрытого или внутреннего поля, оптимизированы для выполнения по номиналу с доступом к полю; незначительное увеличение производительности связано с использованием внешних видимых полей, передаваемых по свойствам.

Видимыми извне называются `public`уровни `protected`доступности, `protected internal` ,`Public`и `Protected`(, `Protected Friend` и в Visual Basic).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, сделайте поле `private` или `internal` предоставьте его с помощью свойства, видимого извне.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Внешние видимые поля не предоставляют никаких преимуществ, недоступных для свойств. Кроме того, открытые поля не могут быть защищены [запросами компоновки](/dotnet/framework/misc/link-demands). См [. раздел CA2112: Защищенные типы не должны предоставлять](../code-quality/ca2112-secured-types-should-not-expose-fields.md)поля.

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