---
title: CA1724. Имена типов не должны совпадать с именами пространства имен
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3554a352cb1c32879397e91dba3ce53f31a14bd0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233855"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724. Имена типов не должны совпадать с именами пространств имен

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Имя типа соответствует имени пространства имен, на которое указывает ссылка, с одним или несколькими видимыми типами извне. При сравнении имен регистр не учитывается.

## <a name="rule-description"></a>Описание правила

Имена созданных пользователем типов не должны совпадать с именами пространств имен, на которые имеются ссылки, которые имеют типы, видимые извне. Нарушение этого правила может снизить удобство использования библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Переименуйте тип таким образом, чтобы он не совпадал с именем упоминаемого пространства имен, которое имеет внешние видимые типы.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для новой разработки нет известных сценариев, при которых необходимо отключить предупреждение из этого правила. Прежде чем подавить предупреждение, тщательно продумайте, как пользователи библиотеки могут быть скрыты по совпадающему имени. Для доставки библиотек может потребоваться отключить предупреждение из этого правила.