---
title: 'CA1806: не игнорировать результаты метода | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543875"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806. Не игнорируйте результаты метода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
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

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если только процесс создания объекта не играет определенной цели.

## <a name="example"></a>Пример
 В следующем примере показан класс, который игнорирует результат вызова String. Trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Пример
 В следующем примере исправляется предыдущее нарушение путем присвоения результата String. Trim к переменной, в которой он был вызван.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Пример
 В следующем примере показан метод, который не использует объект, который он создает.

> [!NOTE]
> Это нарушение не может быть воспроизведено в Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Пример
 Следующий пример устраняет предыдущее нарушение, удаляя ненужное создание объекта.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Пример
 В следующем примере показан метод, который игнорирует код ошибки, возвращаемый собственным методом GetShortPathName.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Пример
 Следующий пример устраняет предыдущее нарушение, проверяя код ошибки и вызывая исключение при сбое вызова.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]