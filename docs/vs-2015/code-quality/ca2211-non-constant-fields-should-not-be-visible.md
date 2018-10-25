---
title: 'CA2211: Неконстантные поля должны быть видимыми | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 62c3ee28a3b7cbb9bef864483e254dda5f63bfae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894258"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: неконстантные поля должны быть скрыты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



