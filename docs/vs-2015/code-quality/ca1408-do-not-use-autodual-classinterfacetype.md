---
title: 'CA1408: Не используйте AutoDual ClassInterfaceType | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 45b9e3b9e562b9b3303d170226845a97af2a0d5a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591312"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: не используйте AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1408: не используйте AutoDual ClassInterfaceType](https://docs.microsoft.com/visualstudio/code-quality/ca1408-do-not-use-autodual-classinterfacetype).

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Отображается тип объектов модели компонентов (COM) помечен с <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут `AutoDual` значение <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Описание правила
 Типы, использующие сдвоенный интерфейс, позволяют клиентам выполнять привязку к определенному макету интерфейса. Все изменения в будущей версии макета типа и в базовых типах приведут к нарушению работы COM-клиентов, связанных с интерфейсом. По умолчанию если <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут не указан, используется интерфейс диспетчеризации.

 Если не указано иное, все открытые неуниверсальные типы являются видимыми для COM; все закрытые и универсальные типы невидимы для модели COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибут `None` значение <xref:System.Runtime.InteropServices.ClassInterfaceType> и явно определяют интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если вы не уверены, что макет типа и его базовых типов не изменится в будущих версиях.

## <a name="example"></a>Пример
 Пример класса, который нарушает правило и повторное объявление класса, чтобы использовать явный интерфейс.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1403: типы с автомакетом не должны быть видимыми для COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: помечайте интерфейсы ComSource как IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>См. также
 [Введение в интерфейс класса](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [уточнение типов .NET для взаимодействия](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



