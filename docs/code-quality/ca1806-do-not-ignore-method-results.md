---
title: CA1806. Не игнорируйте результаты метода
ms.date: 11/04/2016
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
dev_langs:
- CPP
- CSharp
- VB
manager: jillfra
ms.openlocfilehash: 2e68fb6b4c40c165a09ae2631a2ad0a64bf52fbc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921557"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806. Не игнорируйте результаты метода

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Это предупреждение может быть вызвано несколькими причинами.

- Новый объект создается, но не используется.

- Метод, создающий и возвращающий новую строку, вызывается, а новая строка никогда не используется.

- Метод COM или P/Invoke, возвращающий значение HRESULT или код ошибки, который никогда не используется. Описание правила

Создание ненужного объекта и соответствующая сборка мусора неиспользуемого объекта снижает производительность.

Строки являются неизменяемыми, а такие методы, как String. ToUpper, возвращают новый экземпляр строки вместо изменения экземпляра строки в вызывающем методе.

Игнорирование HRESULT или кода ошибки может привести к непредвиденному поведению в условиях ошибки или к нехватке ресурсов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Если метод A создает новый экземпляр объекта B, который никогда не используется, передайте экземпляр в качестве аргумента другому методу или присвойте экземпляр переменной. Если создание объекта не требуется, удалите его.-или-

Если метод A вызывает метод B, но не использует новый экземпляр строки, возвращаемый методом B. Передайте экземпляр в качестве аргумента другому методу, присвойте экземпляр переменной. Или удалите вызов, если он не нужен.

 -или-

Если метод A вызывает метод B, но не использует HRESULT или код ошибки, возвращаемый методом. Используйте результат в условном операторе, присвойте результат переменной или передайте его в качестве аргумента другому методу.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте предупреждение из этого правила, если только процесс создания объекта не играет определенной цели.

## <a name="example"></a>Пример
В следующем примере показан класс, который игнорирует результат вызова String. Trim.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Пример
В следующем примере исправляется предыдущее нарушение путем присвоения результата String. Trim к переменной, в которой он был вызван.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Пример
В следующем примере показан метод, который не использует объект, который он создает.

> [!NOTE]
> Это нарушение не может быть воспроизведено в Visual Basic.

[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Пример
Следующий пример устраняет предыдущее нарушение, удаляя ненужное создание объекта.

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->