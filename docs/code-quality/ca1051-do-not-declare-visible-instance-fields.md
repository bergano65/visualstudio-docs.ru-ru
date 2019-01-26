---
title: CA1051. Не объявляйте видимые поля экземпляров
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 56e5c8f0a0e703bfa2a2cc2419d1bd3be0b0f23a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917229"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051. Не объявляйте видимые поля экземпляров

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит видимое извне экземпляра поле.

## <a name="rule-description"></a>Описание правила
 Поля главным образом следует использовать для данных реализации. Поля должны быть `private` или `internal` и должны быть представлены с помощью свойств. Это так же просто, для доступа к свойству, как получить доступ к полю, а код в методах доступа свойства можно изменить, как расширить возможности типа без нарушения критических изменений. Свойства, которые просто возвращают значение поля закрытого или внутреннего оптимизированы для выполнения наряду с доступом к полю; очень мало выигрыш в производительности, связанный с использование видимого полей по свойствам.

 Видимый извне ссылается на `public`, `protected`, и `protected internal` (`Public`, `Protected`, и `Protected Friend` в Visual Basic) уровни доступности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделать поле `private` или `internal` и предоставите к нему доступ с помощью свойства внешней видимости.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Внешне видимые поля не предоставляют никаких преимуществ, которые недоступны в свойства. Кроме того, открытые поля не могут быть защищены [требования связывания](/dotnet/framework/misc/link-demands). См. в разделе [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Пример
 В следующем примере показано типом (`BadPublicInstanceFields`), нарушает это правило. `GoodPublicInstanceFields` приводится правильный код.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>См. также
 [Требования связывания](/dotnet/framework/misc/link-demands)