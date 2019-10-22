---
title: 'CA2123: запросы компоновки переопределения должны быть идентичны базовым Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bec8f129c094f94ba3eb4021092c402e8263812b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660260"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: запросы компоновки переопределения должны быть идентичны базовым
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не имеет тех же [запросов на компоновку](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) , что и интерфейс или виртуальный метод.

## <a name="rule-description"></a>Описание правила
 Это правило сравнивает метод с его базовым методом (который является интерфейсом или виртуальным методом другого типа), а затем сравнивает запросы ссылок для каждого из них. Нарушение сообщается, если метод или базовый метод имеют запрос компоновки, а другой — нет.

 Если это правило нарушается, вредоносный вызывающий объект может обходить запрос компоновки только путем вызова незащищенного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, примените тот же запрос ссылки к методу или реализации переопределить. Если это невозможно, пометьте метод полным требованием или полностью удалите атрибут.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны различные нарушения этого правила.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>См. также раздел
 Требования к [обеспечению безопасности](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [ссылок](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
