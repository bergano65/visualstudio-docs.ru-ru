---
title: 'CA2112: защищенные типы не должны предоставлять поля | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546540"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112. Защищенные типы не должны предоставлять поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит открытые поля и защищен с помощью [запросов компоновки](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Описание правила
 Если код имеет доступ к экземпляру типа, защищенного запросом компоновки, то для получения доступа к полям типа коду не требуется удовлетворять запросу компоновки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте поля неоткрытыми и добавьте открытые свойства или методы, которые возвращают данные поля. Проверки безопасности LinkDemand для типов защищают доступ к свойствам и методам типа. Однако Управление доступом для кода не применяется к полям.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Как для проблем безопасности, так и для хорошего проектирования, следует устранить нарушения, сделав открытые поля непубличными. Предупреждение из этого правила можно отключить, если в поле не содержатся сведения, которые должны оставаться защищенными, и не полагаться на содержимое поля.

## <a name="example"></a>Пример
 Следующий пример состоит из типа библиотеки ( `SecuredTypeWithFields` ) с незащищенными полями, типа ( `Distributor` ), который может создавать экземпляры типа библиотеки и ошибочно передавать экземпляры в типы, не имеющие разрешения на их создание, а также код приложения, который может считывать поля экземпляра, даже если у него нет разрешения, которое защищает этот тип.

 Следующий код библиотеки нарушает правило.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Пример
 Приложение не может создать экземпляр из-за запроса компоновки, защищающего защищенный тип. Следующий класс позволяет приложению получить экземпляр защищенного типа.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении показано, как, без разрешения на доступ к методам защищенного типа, код может получить доступ к его полям.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 В этом примере формируются следующие данные:

 **Создание экземпляра секуредтипевисфиелдс.** 
 **Поля защищенного типа: 22, 33** 
 **Изменение поля защищенного типа...** 
 **Поля кэшированного объекта: 99, 33**
## <a name="related-rules"></a>Связанные правила
 [CA1051. Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также
 [Данные и моделирование](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [запросов на связывание](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
