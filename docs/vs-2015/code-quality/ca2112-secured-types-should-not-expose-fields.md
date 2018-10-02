---
title: 'CA2112: Защищенные типы не должны предоставлять поля | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a904109e8308eb6984cc00222f2b7861bc0a4f6f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592377"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: защищенные типы не должны предоставлять поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2112: защищенные типы не должны предоставлять поля](https://docs.microsoft.com/visualstudio/code-quality/ca2112-secured-types-should-not-expose-fields).

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытые поля и защищен [требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Описание правила
 Если код имеет доступ к экземпляру типа, защищенного запросом компоновки, то для получения доступа к полям типа коду не требуется удовлетворять запросу компоновки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделать поля неоткрытыми и добавьте открытые свойства или методы, возвращающие данные поля. Проверки безопасности LinkDemand для типов защиты доступа к свойствам и методам типа. Тем не менее доступом для кода не применяется к полям.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Проблемы безопасности и для правильного проектирования необходимо устранить нарушения, сделав nonpublic открытые поля. Можно подавить предупреждение из этого правила, если поле не содержит информации, которую требуется защищать, и вы не зависят от значения поля.

## <a name="example"></a>Пример
 Следующий пример представляет собой тип библиотеки (`SecuredTypeWithFields`) с незащищенными полями, типа (`Distributor`), можно создать экземпляры типа библиотеки и ошибочный передает экземпляров для типов не имеют разрешение на их создание и код приложения, можно прочитать поля экземпляра, несмотря на то, что он не имеет разрешения, который защищает тип.

 Следующий код библиотеки нарушает правило.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Пример
 Приложение не удается создать экземпляр, из-за требования ссылки, защищает тип. Следующий класс позволяет приложению получить экземпляр защищенного типа.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении демонстрируется, как это сделать, без разрешения для доступа к методам защищенного типа, код может обращаться к его полям.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 В этом примере формируются следующие данные:

 **Создание экземпляра SecuredTypeWithFields. ** 
 **Безопасный тип поля: 22, 33**
**изменение защищенного типа поля... ** 
 **Поля объекта кэшируются: 99, 33**
## <a name="related-rules"></a>Связанные правила
 [CA1051: не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также
 [Требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



