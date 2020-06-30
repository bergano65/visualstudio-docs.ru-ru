---
title: 'CA1804: удаление неиспользуемых локальных переменных | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543888"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804. Удалите неиспользуемые локальные переменные
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод объявляет локальную переменную, но не использует переменную, кроме случая, когда получатель оператора присваивания. Для анализа по этому правилу тестируемая сборка должна быть построена с отладочной информацией, а соответствующий файл базы данных программы (PDB) должен быть доступен.

## <a name="rule-description"></a>Описание правила
 Неиспользуемые локальные переменные и ненужные присвоения увеличивают размер сборки и снижают производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или используйте локальную переменную. Обратите внимание, что компилятор C#, включенный в состав, [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] удаляет неиспользуемые локальные переменные при `optimize` включенном параметре.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если переменная была вызвана компилятором. Также можно отключить вывод предупреждений из этого правила или отключать правило, если производительность и обслуживание кода не являются основными проблемами.

## <a name="example"></a>Пример
 В следующем примере показано несколько неиспользуемых локальных переменных.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1809. Избегайте лишних локальных переменных](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811. Избегайте невызываемого частного кода](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812. Избегайте неиспользуемых внутренних классов](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801. Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)
