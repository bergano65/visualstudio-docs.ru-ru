---
title: CA2105. Поля массивов не должны быть доступны только для чтения
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeadbd977b8c7d97af611a2054692a6071f21a36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808306"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105. Поля массивов не должны быть доступны только для чтения

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Открытое или защищенное поле, в котором содержится массив объявлен только для чтения.

## <a name="rule-description"></a>Описание правила

При применении `readonly` (`ReadOnly` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) модификатор к полю, содержащему массив, поле не может изменяться для ссылки в другой массив. Однако элементы массива, хранящегося в доступном только для чтения поле, можно будет изменить. Код, который принимает решения или выполняет операции, основанные на элементы массива только для чтения, могут быть открыты для общего доступа может содержать уязвимые места.

Обратите внимание, что наличие открытое поле также нарушает правило проектирования [CA1051: Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы исправить уязвимость системы безопасности, который определяется этим правилом, не следует полагаться на содержимое массива только для чтения, могут быть открыты для общего доступа. Настоятельно рекомендуется использовать один из следующих процедур:

- Замените массив строго типизированной коллекции, которую нельзя изменить. Дополнительные сведения см. в разделе <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Замените открытое поле с методом, который возвращает клон частного массива. Так как ваш код не полагаться на клоне, отсутствует опасность, если изменение элементов.

Если вы выбрали второй подход, не поменяйте местами поля со свойством; свойства, возвращающие массивы отрицательно повлиять на производительность. Дополнительные сведения см. в разделе [CA1819: Свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Исключения из этого правила предупреждения настоятельно не рекомендуется. Практически ни в каких случаях произойти где несущественны содержимое поля только для чтения. Это делается с помощью сценария, удалить `readonly` модификатор вместо отключения сообщения.

## <a name="example-1"></a>Пример 1

В этом примере показана опасность нарушения этого правила. На первой части показан образец библиотеки, которая имеет тип, `MyClassWithReadOnlyArrayField`, который содержит два поля (`grades` и `privateGrades`), не являются безопасными. Поле `grades` является общим и поэтому подвержен любой вызывающий объект. Поле `privateGrades` является закрытым, но по-прежнему уязвимы, так как он выполняется вызывающим объектам, `GetPrivateGrades` метод. `securePrivateGrades` Предоставляется с безопасным образом `GetSecurePrivateGrades` метод. Он объявляется как закрытые рекомендациям разработки. Вторая часть показан код, который изменяет значения, хранящиеся в `grades` и `privateGrades` членов.

В следующем примере отображается образец библиотеки классов.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Пример 2

В следующем коде используется образец библиотеки классов, чтобы проиллюстрировать проблемы безопасности массива только для чтения.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

Выходные данные из этого примера является:

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>См. также

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>