---
title: 'CA1017: Пометка сборок с помощью ComVisibleAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17f0a540a436316d3a4fb3b71a2a51b1c5a90a6d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535074"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017. Пометьте сборки с помощью ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 К сборке не <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> применен атрибут.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Атрибут определяет, как клиенты COM обращаются к управляемому коду. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM может быть задана для всей сборки, а затем переопределена для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки становится видимым для клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут в сборку. Если вы не хотите, чтобы сборка была видима клиентам COM, примените атрибут и задайте для него значение `false` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если необходимо, чтобы сборка была видимой, примените атрибут и задайте для него значение `true` .

## <a name="example"></a>Пример
 В следующем примере показана сборка с <xref:System.Runtime.InteropServices.ComVisibleAttribute> примененным атрибутом, чтобы предотвратить ее видимость для COM-клиентов.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом,](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [подходящих для взаимодействия типов .NET](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
