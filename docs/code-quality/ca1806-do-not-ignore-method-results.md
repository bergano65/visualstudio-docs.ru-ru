---
title: 'CA1806: не игнорируйте результаты метода'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6b0d5870b29fea9d6ef99a3951ef12d938b0eab3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914670"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: не игнорируйте результаты метода
|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Существует несколько возможных причин для данного предупреждения:

-   Новый объект создается, но никогда не используется.

-   Вызывается метод, который создает и возвращает новую строку, и такая новая строка никогда не используется.

-   Метод COM или P/Invoke возвращает HRESULT или код ошибки, который никогда не используется. Описание правила

 Ненужное создание объекта и связанные мусора для неиспользуемого объекта привести к снижению производительности.

 Строки являются неизменяемыми, и методы как String.ToUpper возвращают новый экземпляр строки, а не вносить изменения в экземпляр строки в вызывающем методе.

 Игнорирование HRESULT или код ошибки может привести к непредвиденному поведению в состоянии ошибки или к нехватке ресурсов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если метод А создает новый экземпляр объекта B, который никогда не используется, передайте этот экземпляр в качестве аргумента другому методу или присвойте экземпляр переменной. Если создание объекта не нужен, удалите его.- или -

 Если метод A вызывает метод B, но не использует новый экземпляр строки, возвращаемый методом B. Передайте этот экземпляр в качестве аргумента другому методу, присвойте экземпляр переменной. Или удалите вызов, если он не нужен.

 - или -

 Если метод A вызывает метод B, но не использует HRESULT или код ошибки, метод возвращает. Используйте результат в условном операторе, присвойте результат переменной или передайте его в качестве аргумента другому методу.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если во время создания объекта служит определенной цели.

## <a name="example"></a>Пример
 Рассмотрим класс, который пропускает результат вызова метода String.Trim.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Пример
 В следующем примере предыдущее нарушение устраняется, назначив результат String.Trim переменную, которую он вызывался.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Пример
 В следующем примере показано метод, который не использует объект, который создает ее.

> [!NOTE]
>  Это нарушение, не могут быть воспроизведены в Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Пример
 В следующем примере предыдущее нарушение устраняется путем удаления ненужных создания объекта.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->