---
title: 'CA2215: Методы Dispose должны вызывать базовый класс | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9115e661b5bd38a23e1429d545d29725a164069a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296885"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: методы Dispose должны вызывать такие же методы базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> наследует от типа, который также реализует <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Не вызывает метод наследующий тип <xref:System.IDisposable.Dispose%2A> метод родительского типа.

## <a name="rule-description"></a>Описание правила
 Если тип наследуется от уничтожаемого типа, он должен вызвать <xref:System.IDisposable.Dispose%2A> метод из базового типа в собственный <xref:System.IDisposable.Dispose%2A> метод. Вызов метода базового типа Dispose гарантирует, что освобождаются все ресурсы, созданные с базовым типом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите `base`.<xref:System.IDisposable.Dispose%2A> в вашей <xref:System.IDisposable.Dispose%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если вызов `base`.<xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правило проверки.

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeA` , реализующий <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeB` , производный от типа `TypeA` и правильно вызывает его <xref:System.IDisposable.Dispose%2A> метод.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.IDisposable?displayProperty=fullName> [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



