---
title: CA2211. Поля, не являющиеся константами, не должны быть видимыми
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 77253de14219c4c1c6737f9bc6e5c61e11fff4ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937469"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211. Поля, не являющиеся константами, не должны быть видимыми

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный статическое поле не является константой и не только для чтения.

## <a name="rule-description"></a>Описание правила
 Для статических полей, которые не являются константными и доступными только для чтения, невозможно обеспечить потокобезопасность. Доступ к подобным полям должен тщательно контролироваться и требуются дополнительные методы программирования для синхронизации доступа к объекту класса. Так как это сложно навыки, чтобы узнать и master и тестирования создает свои собственные сложные задачи, статические поля лучше всего используются для хранения данных, которые не изменяются. Это правило применяется к библиотекам; приложения не должны предоставлять все поля.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте статическое поле, константы или только для чтения. Если это невозможно, измените тип, используемый альтернативный механизм, например поточно-свойство, которое управляет потокобезопасный доступ к базовому полю. Учтите, что проблемы, такие как конфликты блокировок и взаимоблокировок может повлиять на производительность и поведение библиотеки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если вы разрабатываете приложение и поэтому имеют полный контроль над доступом к тип, содержащий статическое поле. Разработчикам библиотек не следует отключать предупреждение из этого правила; Использование статических полей неконстантное может сделать с помощью библиотеки для разработчиков правильно использовать.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]