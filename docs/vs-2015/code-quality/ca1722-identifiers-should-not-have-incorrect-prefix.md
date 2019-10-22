---
title: 'CA1722: идентификаторы не должны иметь неверный префикс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f50c5aca934886f03a54692d98a6be3f8bb5562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671581"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: идентификаторы не должны иметь неверные префиксы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор имеет неверный префикс.

## <a name="rule-description"></a>Описание правила
 В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.

 Имена типов не имеют определенного префикса и не должны начинаться с "C". Это правило сообщает о нарушениях имен типов, таких как "Кмикласс", и не сообщает о нарушениях имен типов, таких как "Cache".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите префикс из идентификатора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1715: идентификаторы должны иметь правильные префиксы](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
