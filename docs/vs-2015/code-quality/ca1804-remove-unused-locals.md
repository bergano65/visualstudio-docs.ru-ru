---
title: CA1804. Удалите неиспользуемые локальные переменные | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38fe76bbdf2fdafa69ca12caf4f131a05f783954
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143116"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804. Удалите неиспользуемые локальные переменные
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод объявляет локальную переменную, но не использует переменную, за исключением возможно как получатель части оператора присваивания. Для анализа этим правилом протестированных сборки должны быть построены с отладочной информацией и связанный PDB-файл должен быть доступен.

## <a name="rule-description"></a>Описание правила
 Неиспользуемые локальные переменные и ненужные присвоения увеличивают размер сборки и снижают производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или использовать локальную переменную. Обратите внимание, что компилятор C#, входит в состав [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] удаляет неиспользуемые локальные переменные при `optimize` включен параметр.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если переменная создана компилятором. Можно также безопасно подавить предупреждение из этого правила, или отключить правило, если производительность и обслуживание кода не являются критичными моментами.

## <a name="example"></a>Пример
 В следующем примере показано несколько неиспользуемые локальные переменные.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1809: Избегайте чрезмерного использования локальных переменных](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Не используйте Невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)
