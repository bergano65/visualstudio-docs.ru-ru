---
title: 'CA2105: поля массивов не должны быть доступны только для чтения'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91a97983a8760d7f5df04fe6e5b0a56a782a11ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915210"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: поля массивов не должны быть доступны только для чтения
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный поле, которое хранит массив объявлен только для чтения.

## <a name="rule-description"></a>Описание правила
 При применении `readonly` (`ReadOnly` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) модификатор к полю, содержащему массив, это поле нельзя ссылаться в другой массив. Однако элементы массива, хранящегося в доступном только для чтения поле, можно будет изменить. Код, который принимает решения или выполняет операции, основанные на элементы массива только для чтения, могут быть открыты для общего доступа может содержать уязвимые места.

 Обратите внимание, что открытое поле с также нарушает правило проектирования [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить уязвимость системы безопасности, который определен с помощью этого правила, не следует полагаться на содержимое массива только для чтения, могут быть открыты для общего доступа. Настоятельно рекомендуется использовать один из следующих процедур:

-   Замените массив строго типизированную коллекцию, которую нельзя изменить. Дополнительные сведения см. в разделе <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Замените открытое поле методом, который возвращает клон частного массива. Поскольку код не использует копию, отсутствует опасность, если элементы были изменены.

 Если вы выбрали второй вариант, следует заменять поле свойством; свойства, возвращающие массивы отрицательно повлиять на производительность. Дополнительные сведения см. в разделе [CA1819: свойства не должны возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 При исключении предупреждение из этого правила настоятельно не рекомендуется. Практически ни в каких случаях возникают, где значения только для чтения поля не имеют значения. Если это относится к сценарию удалить `readonly` модификатор вместо отключения сообщения.

## <a name="example"></a>Пример
 В этом примере показана опасность нарушения этого правила. В первой части показывается образец библиотеки, который имеет тип, `MyClassWithReadOnlyArrayField`, содержит два поля (`grades` и `privateGrades`), не являются безопасными. Поле `grades` является открытым и, следовательно, уязвимым к любой вызывающий объект. Поле `privateGrades` является закрытым, но по-прежнему уязвимой, так как он возвращается к вызывающим объектам, `GetPrivateGrades` метод. `securePrivateGrades` Предоставляется безопасным образом, `GetSecurePrivateGrades` метод. Он объявляется как закрытые рекомендациям разработки. Вторая часть показывает код, который изменяет значения, хранящиеся в `grades` и `privateGrades` члены.

 В следующем примере отображается образец библиотеки классов.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Пример
 В следующем коде используется образец библиотеки классов для иллюстрации проблемы безопасности массива только для чтения.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 Выходные данные в этом примере будут:

 **Перед подмены: оценок: 90, 90, 90 оценок закрытого: 90, 90, 90 Secure оценками 90, 90, 90**
**после подмены: оценок: 90, 555, 90 оценок закрытого: 90, 555, 90 Secure оценками 90, 90, 90**
## <a name="see-also"></a>См. также
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>