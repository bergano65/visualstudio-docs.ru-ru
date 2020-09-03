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
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540664"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220. Методы завершения должны вызывать метод завершения базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, переопределяющий, <xref:System.Object.Finalize%2A?displayProperty=fullName> не вызывает <xref:System.Object.Finalize%2A> метод в его базовом классе.

## <a name="rule-description"></a>Описание правила
 Финализация должна распространятся посредством иерархии наследования. Чтобы убедиться в этом, типы должны вызывать свой метод базового класса <xref:System.Object.Finalize%2A> из своего собственного <xref:System.Object.Finalize%2A> метода. Компилятор C# автоматически добавляет вызов метода завершения базового класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите метод базового типа <xref:System.Object.Finalize%2A> из <xref:System.Object.Finalize%2A> метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, нацеленные на среду CLR, вставляют вызов метода завершения базового типа в промежуточный язык Майкрософт (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и его необходимо добавить в код.

## <a name="example"></a>Пример
 В следующем примере Visual Basic показан тип `TypeB` , который правильно вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также:
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
