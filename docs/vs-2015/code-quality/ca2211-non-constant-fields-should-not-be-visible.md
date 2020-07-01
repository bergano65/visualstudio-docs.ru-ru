---
title: 'CA2211: поля, не являющиеся константами, не должны быть видимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa67c33eac5d618c0a080323720775beea7b68c3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548217"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211. Поля, не являющиеся константами, не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытое или защищенное статическое поле не является константой и не предназначено только для чтения.

## <a name="rule-description"></a>Описание правила
 Для статических полей, которые не являются константными и доступными только для чтения, невозможно обеспечить потокобезопасность. Доступ к такому полю должен быть тщательно контролируемым и требует расширенных методов программирования для синхронизации доступа к объекту класса. Поскольку они являются сложными навыками для изучения и настройки и тестирования такого объекта являются собственными задачами, статические поля лучше использовать для хранения данных, которые не изменяются. Это правило применяется к библиотекам; приложения не должны предоставлять какие бы то ни было поля.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте константу статического поля или только для чтения. Если это невозможно, переработайте тип для использования альтернативного механизма, такого как поточно-ориентированное свойство, которое управляет потокобезопасным доступом к базовому полю. Учтите, что такие проблемы, как состязание за блокировку и взаимоблокировки, могут повлиять на производительность и поведение библиотеки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы разрабатываете приложение и имеете полный контроль над доступом к типу, содержащему статическое поле. Дизайнеры библиотек не должны подавлять предупреждение из этого правила. Использование неконстантных статических полей может усложнить использование библиотеки разработчиками для правильной работы.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
