---
title: 'CA2211: Неконстантные поля должны быть видимыми | Документация Майкрософт'
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
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d6ad55a49d335f5f776ba7b75f8006559e0eb38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591929"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: неконстантные поля должны быть скрыты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2211: Неконстантные поля не должны быть видимыми](https://docs.microsoft.com/visualstudio/code-quality/ca2211-non-constant-fields-should-not-be-visible).

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

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



