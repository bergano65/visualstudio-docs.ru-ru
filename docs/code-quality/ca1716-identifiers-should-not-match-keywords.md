---
title: CA1716. Идентификаторы не должны совпадать с ключевыми словами
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb483206ba13f89f0a23667039bf5f1a9d740b73
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910199"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716. Идентификаторы не должны совпадать с ключевыми словами

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя пространства имен, тип или член виртуального члена или интерфейс совпадает с зарезервированным ключевым словом в языке программирования.

## <a name="rule-description"></a>Описание правила

Идентификаторы пространств имен, типов и виртуальные и члены интерфейса не должны совпадать с ключевыми словами, которые определены в языках, поддерживаемых среда CLR. В зависимости от используемого языка и ключевого слова ошибки компилятора и неоднозначностей могут затруднять библиотеку для использования.

Это правило проверяет ключевые слова на следующих языках:

- Visual Basic

- C#

- C++/CLI

Сравнение без учета регистра, используемый для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ключевые слова и сравнение с учетом регистра используется для других языков.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Выберите имя, которое не отображается в списке ключевых слов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно подавить предупреждение из этого правила, если вы уверены, что идентификатор не будет запутывания пользователей API-интерфейса, и что библиотеки можно использовать в некоторых языках платформы .NET Framework.