---
title: CA2112. Защищенные типы не должны предоставлять поля
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d46c9fe1b97b5bdfb081150a44aa69363eced53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808235"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112. Защищенные типы не должны предоставлять поля

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытые поля и защищен [требования связывания](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Описание правила
 Если код имеет доступ к экземпляру типа, защищенного запросом компоновки, то для получения доступа к полям типа коду не требуется удовлетворять запросу компоновки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделать поля неоткрытыми и добавьте открытые свойства или методы, возвращающие данные поля. Проверки безопасности LinkDemand для типов защиты доступа к свойствам и методам типа. Тем не менее доступом для кода не применяется к полям.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Проблемы безопасности и для правильного проектирования необходимо устранить нарушения, сделав nonpublic открытые поля. Можно подавить предупреждение из этого правила, если поле не содержит информации, которую требуется защищать, и вы не зависят от значения поля.

## <a name="example"></a>Пример
 Следующий пример представляет собой тип библиотеки (`SecuredTypeWithFields`) с незащищенными полями, типа (`Distributor`), можно создать экземпляры типа библиотеки и ошибочный передает экземпляров для типов не имеют разрешение на их создание и код приложения, можно прочитать поля экземпляра, несмотря на то, что он не имеет разрешения, который защищает тип.

 Следующий код библиотеки нарушает правило.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Пример 1
 Приложение не удается создать экземпляр, из-за требования ссылки, защищает тип. Следующий класс позволяет приложению получить экземпляр защищенного типа.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Пример 2
 В следующем приложении демонстрируется, как это сделать, без разрешения для доступа к методам защищенного типа, код может обращаться к его полям.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

В этом примере выводятся следующие данные:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Связанные правила

- [CA1051: Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также

- [Требования связывания](/dotnet/framework/misc/link-demands)
- [Данные и моделирование](/dotnet/framework/data/index)