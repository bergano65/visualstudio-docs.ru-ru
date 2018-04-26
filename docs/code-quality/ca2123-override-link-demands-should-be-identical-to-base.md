---
title: 'CA2123: запросы компоновки переопределения должны быть идентичны базовым'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340b0e7deb12d4568a76d4871eabd49641926dcb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: запросы компоновки переопределения должны быть идентичны базовым
|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не с одинаковыми [требования связывания](/dotnet/framework/misc/link-demands) как интерфейс или виртуальный метод.

## <a name="rule-description"></a>Описание правила
 Это правило сравнивает метод с его базовым методом (который является интерфейсом или виртуальным методом другого типа), а затем сравнивает запросы ссылок для каждого из них. Нарушение сообщается, если метод или метод базового содержит запрос компоновки, а другой — нет.

 Если это правило нарушается, то вредоносный вызывающий объект может обойти запрос ссылок путем вызова небезопасного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, примените то же требование ссылки к переопределению метода или реализации. Если это невозможно, пометьте метод полным требованием или полностью удалить атрибут.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано различные нарушения этого правила.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines) [требования связывания](/dotnet/framework/misc/link-demands)