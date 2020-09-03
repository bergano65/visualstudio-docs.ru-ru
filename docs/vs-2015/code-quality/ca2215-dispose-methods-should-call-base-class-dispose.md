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
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534385"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215. Метод Dispose должен вызывать базовый класс Dispose
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> наследование от типа, который также реализует <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Метод наследуемого типа не вызывает <xref:System.IDisposable.Dispose%2A> метод родительского типа.

## <a name="rule-description"></a>Описание правила
 Если тип наследуется от удаляемого типа, он должен вызывать <xref:System.IDisposable.Dispose%2A> метод базового типа из собственного <xref:System.IDisposable.Dispose%2A> метода. Вызов метода базового типа Dispose гарантирует освобождение всех ресурсов, созданных базовым типом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите метод `base` .<xref:System.IDisposable.Dispose%2A> в <xref:System.IDisposable.Dispose%2A> методе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 При вызове функции можно отключить вывод предупреждений из этого правила `base` .<xref:System.IDisposable.Dispose%2A> происходит на уровне более глубокого вызова по сравнению с проверкой правил.

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeA` , реализующий интерфейс <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeB` , который наследует от типа `TypeA` и правильно вызывает его <xref:System.IDisposable.Dispose%2A> метод.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также:
 <xref:System.IDisposable?displayProperty=fullName> [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
