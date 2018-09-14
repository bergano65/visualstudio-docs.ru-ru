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
ms.openlocfilehash: ebb37743f9259390aba400a5d89d24b5f41a0d49
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546984"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: запросы компоновки переопределения должны быть идентичны базовым

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не имеют одинаковые [требования связывания](/dotnet/framework/misc/link-demands) как интерфейс или виртуальный метод.

## <a name="rule-description"></a>Описание правила
 Это правило сравнивает метод с его базовым методом (который является интерфейсом или виртуальным методом другого типа), а затем сравнивает запросы ссылок для каждого из них. Нарушение отмечается в том случае, если метод или метод базового содержит запрос компоновки, а другой — нет.

 Если это правило нарушается, злонамеренный вызывающий объект может обойти запрос ссылок путем вызова небезопасного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените то же требование ссылки переопределение метода или реализации. Если это невозможно, пометьте метод полное требование или полностью удалить атрибут.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает различные нарушения этого правила.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>См. также

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Требования связывания](/dotnet/framework/misc/link-demands)