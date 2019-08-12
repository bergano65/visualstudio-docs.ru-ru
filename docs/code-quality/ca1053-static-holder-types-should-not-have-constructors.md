---
title: CA1053. Типы со статическими заполнителями не должны иметь конструкторы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fec59e1d683c7867eb1cad9ae4e796a0815200d4
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604781"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053. Типы статических владельцев не должны иметь конструкторов по умолчанию

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

> [!NOTE]
> Правило CA1053 объединено в [CA1052: Типы со статическими заполнителями должны](ca1052-static-holder-types-should-be-sealed.md) быть запечатаны в [анализаторах FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Причина

Открытый или вложенный открытый тип объявляет только статические члены и имеет конструктор по умолчанию.

## <a name="rule-description"></a>Описание правила

Конструктор по умолчанию не нужен, так как для вызова статических членов не требуется экземпляр типа. Кроме того, поскольку тип не имеет нестатических членов, создание экземпляра не обеспечивает доступ ни к одному из членов типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите конструктор по умолчанию.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Наличие конструктора по умолчанию предполагает, что тип не является статическим.