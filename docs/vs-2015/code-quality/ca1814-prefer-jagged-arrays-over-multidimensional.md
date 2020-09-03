---
title: 'CA1814: предпочитать массивы в многомерном виде | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ece9105e8a0a854837924e4a2d4f4ec485a5e202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543940"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814. Используйте массивы массивов вместо многомерных массивов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Категория|Microsoft. Performance|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Член объявляется как многомерный массив.

## <a name="rule-description"></a>Описание правила
 Массив массивов — это массив, элементы которого сами являются массивами. Массивы, которые составляют элементы, могут иметь различные размеры, что позволяет экономить пространство для некоторых наборов данных.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените многомерный массив на массив массива.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если в многомерном массиве не тратится место.

## <a name="example"></a>Пример
 В следующем примере показаны объявления для массивов неровных и многомерных массивов.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
