---
title: CA2220. Методы завершения должны вызывать метод завершения базового класса | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 432d973a64c7ee7f4264841e2a1277f66c9259da
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979116"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220. Методы завершения должны вызывать метод завершения базового класса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, который переопределяет <xref:System.Object.Finalize%2A?displayProperty=fullName> не вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.

## <a name="rule-description"></a>Описание правила
 Финализация должна распространятся посредством иерархии наследования. Для этого типы должны вызывать базовый класс <xref:System.Object.Finalize%2A> метода в свои собственные <xref:System.Object.Finalize%2A> метод. Компилятор C# автоматически добавляет вызов метод завершения базового класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите базовый тип <xref:System.Object.Finalize%2A> метода из вашей <xref:System.Object.Finalize%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Некоторые компиляторы, предназначенные среда CLR вставьте вызов метод завершения базового типа в промежуточный язык Майкрософт (MSIL). Если выводится предупреждение из этого правила, компилятор не вставляет вызов, и его необходимо добавить в код.

## <a name="example"></a>Пример
 В следующем примере Visual Basic показан тип `TypeB` , правильно вызывает <xref:System.Object.Finalize%2A> метод в базовом классе.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>См. также
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
