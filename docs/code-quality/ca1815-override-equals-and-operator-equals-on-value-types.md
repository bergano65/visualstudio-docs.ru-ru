---
title: CA1815. Переопределяйте операторы Equals и равенства для типов значений
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c4cf84a292e11b20eb37bee562cd039096e56af
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873429"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815. Переопределяйте операторы Equals и равенства для типов значений

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип значения не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не реализует оператор равенства (==). Это правило не проверяет перечисления.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Для типов значений, унаследованной реализации <xref:System.Object.Equals%2A> используется библиотека отражения и сравнивается содержимое всех полей. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если ожидается, что пользователи сравнение и сортировка экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, предоставлять реализацию метода <xref:System.Object.Equals%2A>. Если вы можете реализуйте оператор равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если экземпляры типа значения не будут сравниваться друг с другом.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1815.api_surface = private, internal
```

В этой категории (производительность), можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

Приведенный ниже показана структура (тип значения), который нарушает это правило:

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

Следующий код предыдущее нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName> и реализации операторов равенства (==,! =):

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>См. также

- <xref:System.Object.Equals%2A?displayProperty=fullName>