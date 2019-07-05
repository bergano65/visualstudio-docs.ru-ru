---
title: CA1806. Не игнорируйте результаты метода | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 117e26fca367c8cf00604bebe01a00f4df58a0ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437398"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806. Не игнорируйте результаты метода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Это предупреждение может быть вызвана несколькими причинами:  
  
- Новый объект создается, но никогда не используется.  
  
- Вызывается метод, который создает и возвращает новую строку, и новая строка никогда не используется.  
  
- Метод COM или P/Invoke возвращает HRESULT или код ошибки, который никогда не используется. Описание правила  
  
  Ненужное создание объекта и связанной сборке мусора неиспользуемого объекта привести к снижению производительности.  
  
  Строки являются неизменяемыми, и методы, такие как String.ToUpper возвращает новый экземпляр строки, а не вносить изменения в экземпляр строки в вызывающем методе.  
  
  Пропуск HRESULT или код ошибки может привести к непредвиденному поведению в состоянии ошибки или к нехватке ресурсов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Если метод А создает новый экземпляр объекта B, который никогда не используется, передайте экземпляр в качестве аргумента другому методу или присвойте экземпляр переменной. Если создание объекта не нужен, удалите его.- или -  
  
 Если метод A вызывает метод B, но не использует новый экземпляр строки, возвращаемое методом, B. Передайте экземпляр в качестве аргумента другому методу, присвойте экземпляр переменной. Или удалите вызов, если он не нужен.  
  
 -или-  
  
 Если метод A вызывает метод B, но не использует HRESULT или код ошибки, метод возвращает. Используйте результат в условном операторе, присвоить результат переменной или передайте его в качестве аргумента другому методу.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, если процесс создания объекта служит определенной цели.  
  
## <a name="example"></a>Пример  
 В следующем примере показан класс, игнорирующий результат вызова метода String.Trim.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Пример  
 В следующем примере устраняется предыдущее нарушение, назначив результат String.Trim переменной, в котором он вызывался.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Пример  
 Пример метода, использует ли объект, он создает.  
  
> [!NOTE]
> Это нарушение невозможно воспроизвести в Visual Basic.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Пример  
 В следующем примере устраняется нарушение устраняется путем удаления ненужных создания объекта.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Пример  
 Пример метода, который не учитывает собственным методом GetShortPathName код ошибки.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Пример  
 В следующем примере устраняется нарушение устраняется путем проверки кода ошибки и исключения, при сбое вызова.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]