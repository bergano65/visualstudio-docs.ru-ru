---
title: 'CA1051: Не объявляйте видимые поля экземпляров | Документация Майкрософт'
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
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43edecc9b5e5f4aa662f30dc1ac84a5e8c3b991e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591873"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: не объявляйте видимые поля экземпляров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1051: не объявляйте видимые поля экземпляров](https://docs.microsoft.com/visualstudio/code-quality/ca1051-do-not-declare-visible-instance-fields).

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
 Для этого правила отключать вывод предупреждений не следует. Внешне видимые поля не предоставляют никаких преимуществ, которые недоступны в свойства. Кроме того, открытые поля не могут быть защищены [требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). См. в разделе [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Пример
 В следующем примере показано типом (`BadPublicInstanceFields`), нарушает это правило. `GoodPublicInstanceFields` приводится правильный код.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>См. также
 [Требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



