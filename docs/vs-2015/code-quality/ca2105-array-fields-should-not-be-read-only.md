---
title: 'CA2105: поля массива не должны быть доступны только для чтения | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7599359899ca4860913b5bc0dd601fd06d9b8b54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666015"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: поля массивов не должны быть доступны только для чтения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытое или защищенное поле, содержащее массив, объявлено как доступное только для чтения.

## <a name="rule-description"></a>Описание правила
 При применении модификатора `readonly` (`ReadOnly` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) к полю, содержащему массив, поле нельзя изменить, чтобы оно ссылалось на другой массив. Однако элементы массива, хранящегося в доступном только для чтения поле, можно будет изменить. Код, который принимает решения или выполняет операции, основанные на элементах доступного только для чтения массива, к которому можно получить доступ, может содержать уязвимую уязвимость системы безопасности.

 Обратите внимание, что наличие открытого поля также нарушает правило разработки [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить уязвимость системы безопасности, определенную этим правилом, не следует полагаться на содержимое доступного только для чтения массива, доступ к которому может быть открыт. Настоятельно рекомендуется использовать одну из следующих процедур.

- Замените массив строго типизированной коллекцией, которую нельзя изменить. Дополнительные сведения см. в разделе <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Замените открытое поле методом, который возвращает клон закрытого массива. Так как код не зависит от клона, при изменении элементов отсутствует опасность.

  Если вы выбрали второй подход, не заменяйте поле свойством; свойства, возвращающие массивы, неблагоприятно влияют на производительность. Дополнительные сведения см. в разделе [CA1819: Properties не должен возвращать массивы](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключение предупреждения из этого правила настоятельно не рекомендуется. Практически нет ситуаций, когда содержимое поля, доступного только для чтения, не имеет значения. Если в вашем сценарии это так, удалите модификатор `readonly`, не исключая сообщение.

## <a name="example"></a>Пример
 В этом примере демонстрируются опасности нарушения этого правила. В первой части показан пример библиотеки с типом `MyClassWithReadOnlyArrayField`, который содержит два поля (`grades` и `privateGrades`), которые не являются безопасными. Поле `grades` является общедоступным и, следовательно, уязвимым для любого вызывающего. Поле `privateGrades` является закрытым, но по-прежнему уязвимо, так как оно возвращается вызывающим объектам методом `GetPrivateGrades`. `securePrivateGrades` поле предоставляется в безопасном порядке методом `GetSecurePrivateGrades`. Он объявляется как частный, чтобы соответствовать хорошим рекомендациям по проектированию. Во второй части показан код, который изменяет значения, хранящиеся в `grades` и `privateGrades` элементов.

 Пример библиотеки классов показан в следующем примере.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Пример
 В следующем коде используется пример библиотеки классов для иллюстрации проблем безопасности массива, доступного только для чтения.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Выходные данные этого примера:

 **Перед незаконным изменением: оценки: 90, 90, 90 частные оценки: 90, 90, 90 Secure Grades, 90, 90, 90**
**после незаконного изменения: оценки: 90, 555, 90 Private grades: 90, 555, 90 Secure grades, 90, 90, 90**
## <a name="see-also"></a>См. также
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
