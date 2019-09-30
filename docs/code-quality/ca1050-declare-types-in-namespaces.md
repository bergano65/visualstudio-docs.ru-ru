---
title: CA1050. Объявите типы в пространствах имен
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8127c68cfe7eb541b8adea8affad99027e0c1fe7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235752"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050. Объявите типы в пространствах имен

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Открытый или защищенный тип определен вне области именованного пространства имен.

## <a name="rule-description"></a>Описание правила
Типы объявляются в пространствах имен для предотвращения конфликтов имен, а также как способ организации связанных типов в иерархии объектов. Типы, находящиеся за пределами именованного пространства имен, находятся в глобальном пространстве имен, на которое нельзя ссылаться в коде.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, разместите тип в пространстве имен.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Несмотря на то, что не нужно отключать предупреждение из этого правила, это можно сделать в том случае, если сборка никогда не будет использоваться вместе с другими сборками.

## <a name="example"></a>Пример
В следующем примере показана библиотека с типом, неверно объявленным вне пространства имен, и типом с тем же именем, объявленным в пространстве имен.

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Пример
В следующем приложении используется библиотека, определенная ранее. Обратите внимание, что тип, объявленный вне пространства имен, создается, `Test` когда имя не уточняется пространством имен. Обратите внимание, что для `Test` доступа к `Goodspace`типу в необходимо указать имя пространства имен.

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]