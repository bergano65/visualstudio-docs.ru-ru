---
title: 'CA2116: Методы APTCA должны вызывать только методы APTCA | Документация Майкрософт'
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
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 78e3136ed2671de2962ae4de994bae178fcbceca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591669"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: методы APTCA должны вызывать только методы APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2116: методы APTCA должны вызывать только методы APTCA](https://docs.microsoft.com/visualstudio/code-quality/ca2116-aptca-methods-should-only-call-aptca-methods).

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод в сборке с <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> атрибута вызывает метод в сборке, которая не имеет атрибута.

## <a name="rule-description"></a>Описание правила
 По умолчанию, открытые или защищенные методы в сборках со строгими именами неявно защищены [требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) для полного доверия; только полностью доверенные, вызывающие объекты могут получить доступ к является сборкой со строгим именем. Сборки со строгими именами, имеющие <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA) нет эту защиту. Атрибут отключает компоновки, доступности сборки вызывающим объектам, не имеющие полного доверия, например код, выполнение из интрасети или Интернета.

 Если в полностью доверенной сборке присутствует атрибут APTCA, и она выполняет код в другой сборке, которая не позволяет частично доверенным вызывающим объектам, возможен уязвимости безопасности. Если два метода `M1` и `M2` удовлетворять следующим условиям, злоумышленники могут использовать метод `M1` обходить требование связывания неявное полного доверия, который защищает `M2`:

-   `M1` открытый метод, объявленный в полностью доверенной сборке, помеченной атрибутом APTCA.

-   `M1` вызывает метод `M2` за пределами `M1`в сборку.

-   `M2`в сборки не имеет атрибута APTCA и, таким образом, не будет выполнена, или от имени частично доверенных вызывающих.

 Частично доверенного вызывающего `X` можно вызвать метод `M1`, вызывающие `M1` для вызова `M2`. Так как `M2` не имеет атрибута APTCA, его непосредственный вызывающий объект (`M1`) должен удовлетворять запрос ссылки для полного доверия; `M1` имеет полное доверие и пройти проверку. Угроза безопасности возникает, так как `X` не участвует в выполнении требования ссылки, которая защищает `M2` от ненадежных вызывающих объектов. Таким образом методы с атрибутом APTCA не должны вызывать методы, не имеющие атрибута.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если требуется атрибут APCTA, используйте требование для защиты метода, вызывающего сборку с полным доверием. Точные разрешения, вы запросу будет зависеть от функциональности, предоставляемой методом. Если это возможно, следует Защитите метод требование полного доверия, чтобы убедиться, что частично доверенным вызывающим объектам не предоставляется базовая функциональность. Если это невозможно, выберите набор разрешений, защищающий функциональные возможности. Дополнительные сведения о требованиях см. в разделе [требования](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно подавить предупреждение из этого правила, необходимо убедиться, что функции, предоставляемые ваш метод прямо или косвенно позволяет вызывающим объектам доступ к конфиденциальной информации, операции или ресурсы, которые могут использоваться в злонамеренных целях.

## <a name="example"></a>Пример
 В следующем примере две сборки и тестовое приложение для демонстрации уязвимости системы безопасности, обнаруживаемый этим правилом. Первая сборка не имеет атрибута APTCA и не должны быть доступны частично доверенным вызывающим объектам (представленный `M2` в описании выше).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Пример
 Вторая сборка является полностью доверенной и позволяет частично доверенным вызывающим объектам (представленный `M1` в описании выше).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Пример
 Тестовое приложение (представленный `X` в предыдущем описании) является частично доверенным.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 В этом примере формируются следующие данные:

 **Требование полного доверия: запрос не удалось. ** 
 **ClassRequiringFullTrust.DoWork был вызван.**
## <a name="related-rules"></a>Связанные правила
 [CA2117: APTCA-типы должны расширять только базовые APTCA-типы](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>См. также
 [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [сборки .NET Framework, вызываться частично доверенного кода](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [использование библиотек из частично доверенного кода](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [требования](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [данные и моделирование](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



