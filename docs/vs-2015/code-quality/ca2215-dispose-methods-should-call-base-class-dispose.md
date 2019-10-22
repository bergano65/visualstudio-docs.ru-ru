---
title: 'CA2215: методы Dispose должны вызывать базовый класс Dispose | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662852"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: методы Dispose должны вызывать такие же методы базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName>, наследуется от типа, который также реализует <xref:System.IDisposable>. Метод <xref:System.IDisposable.Dispose%2A> наследуемого типа не вызывает метод <xref:System.IDisposable.Dispose%2A> родительского типа.

## <a name="rule-description"></a>Описание правила
 Если тип наследуется от удаляемого типа, он должен вызвать метод <xref:System.IDisposable.Dispose%2A> базового типа из собственного метода <xref:System.IDisposable.Dispose%2A>. Вызов метода базового типа Dispose гарантирует освобождение всех ресурсов, созданных базовым типом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите `base`. <xref:System.IDisposable.Dispose%2A> в методе <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждений из этого правила, если вызов `base`. <xref:System.IDisposable.Dispose%2A> происходит на уровне более глубокого вызова по сравнению с проверкой правил.

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeA`, который реализует <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeB`, который наследуется от типа `TypeA` и правильно вызывает метод <xref:System.IDisposable.Dispose%2A>.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также раздел
 [шаблон удаления](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
