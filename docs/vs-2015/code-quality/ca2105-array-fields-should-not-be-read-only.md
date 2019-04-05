---
title: CA2105. Поля массивов не должны считываться только | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4741b30d1429a1a179328c8fb4b150fc4f920612
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992058"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105. Поля массивов не должны быть доступны только для чтения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытое или защищенное поле, в котором содержится массив объявлен только для чтения.

## <a name="rule-description"></a>Описание правила
 При применении `readonly` (`ReadOnly` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) модификатор к полю, содержащему массив, поле не может изменяться для ссылки в другой массив. Однако элементы массива, хранящегося в доступном только для чтения поле, можно будет изменить. Код, который принимает решения или выполняет операции, основанные на элементы массива только для чтения, могут быть открыты для общего доступа может содержать уязвимые места.

 Обратите внимание, что наличие открытое поле также нарушает правило проектирования [CA1051: Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы исправить уязвимость системы безопасности, который определяется этим правилом, не следует полагаться на содержимое массива только для чтения, могут быть открыты для общего доступа. Настоятельно рекомендуется использовать один из следующих процедур:

- Замените массив строго типизированной коллекции, которую нельзя изменить. Дополнительные сведения см. в разделе <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Замените открытое поле с методом, который возвращает клон частного массива. Так как ваш код не полагаться на клоне, отсутствует опасность, если изменение элементов.

  Если вы выбрали второй подход, не поменяйте местами поля со свойством; свойства, возвращающие массивы отрицательно повлиять на производительность. Дополнительные сведения см. в разделе [CA1819: Свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключения из этого правила предупреждения настоятельно не рекомендуется. Практически ни в каких случаях произойти где несущественны содержимое поля только для чтения. Это делается с помощью сценария, удалить `readonly` модификатор вместо отключения сообщения.

## <a name="example"></a>Пример
 В этом примере показана опасность нарушения этого правила. На первой части показан образец библиотеки, которая имеет тип, `MyClassWithReadOnlyArrayField`, который содержит два поля (`grades` и `privateGrades`), не являются безопасными. Поле `grades` является общим и поэтому подвержен любой вызывающий объект. Поле `privateGrades` является закрытым, но по-прежнему уязвимы, так как он выполняется вызывающим объектам, `GetPrivateGrades` метод. `securePrivateGrades` Предоставляется с безопасным образом `GetSecurePrivateGrades` метод. Он объявляется как закрытые рекомендациям разработки. Вторая часть показан код, который изменяет значения, хранящиеся в `grades` и `privateGrades` членов.

 В следующем примере отображается образец библиотеки классов.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Пример
 В следующем коде используется образец библиотеки классов, чтобы проиллюстрировать проблемы безопасности массива только для чтения.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Выходные данные из этого примера является:

 **Прежде чем незаконное изменение: Оценки: 90, 90, 90 private оценок: 90, 90, 90 secure оценками 90, 90, 90**
**после изменения: Оценки: 90, 555, 90 private оценок: 90, 555, 90 secure оценок, 90, 90, 90**
## <a name="see-also"></a>См. также
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
