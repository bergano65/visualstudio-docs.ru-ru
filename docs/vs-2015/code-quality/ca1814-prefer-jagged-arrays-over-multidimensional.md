---
title: CA1814. Используйте массивы массивов вместо многомерных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 73b20ef9a93e59f3fae30407deda8d21befc57f5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993409"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814. Используйте массивы массивов вместо многомерных массивов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Категория|Microsoft.Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Член объявлен как многомерный массив.

## <a name="rule-description"></a>Описание правила
 Массив массивов — это массив, элементы которого сами являются массивами. Массивы, которые составляют элементы, могут иметь различные размеры, что позволяет экономить пространство для некоторых наборов данных.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените многомерного массива в массив массивов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если многомерный массив не расходует место.

## <a name="example"></a>Пример
 В следующем примере показано объявление массивов и многомерные массивы.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
