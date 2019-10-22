---
title: 'CA2220: методы завершения должны вызывать метод завершения базового класса | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663579"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: методы завершения должны вызывать метод завершения базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, переопределяющий <xref:System.Object.Finalize%2A?displayProperty=fullName>, не вызывает метод <xref:System.Object.Finalize%2A> в его базовом классе.

## <a name="rule-description"></a>Описание правила
 Финализация должна распространятся посредством иерархии наследования. Чтобы убедиться в этом, типы должны вызывать свой базовый класс <xref:System.Object.Finalize%2A> метод из своего собственного метода <xref:System.Object.Finalize%2A>. C# Компилятор автоматически добавляет вызов метода завершения базового класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите метод <xref:System.Object.Finalize%2A> базового типа из метода <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, нацеленные на среду CLR, вставляют вызов метода завершения базового типа в промежуточный язык Майкрософт (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и его необходимо добавить в код.

## <a name="example"></a>Пример
 В следующем примере Visual Basic показан `TypeB` типа, который правильно вызывает метод <xref:System.Object.Finalize%2A> в своем базовом классе.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также раздел
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
