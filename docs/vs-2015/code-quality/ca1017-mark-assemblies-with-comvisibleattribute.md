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
ms.openlocfilehash: 505e5780b8a50113aaf98ea7dbac767d280bebb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662059"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: помечайте сборки атрибутом ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 К сборке не применен атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> определяет, как клиенты COM обращаются к управляемому коду. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM может быть задана для всей сборки, а затем переопределена для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки становится видимым для клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут в сборку. Если вы не хотите, чтобы сборка была видима клиентам COM, примените атрибут и присвойте ему значение `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если необходимо, чтобы сборка была видимой, примените атрибут и присвойте ему значение `true`.

## <a name="example"></a>Пример
 В следующем примере показана сборка с примененным атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute>, чтобы предотвратить его видимость для COM-клиентов.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>См. также раздел
 [Взаимодействие с неуправляемым кодом,](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [подходящих для взаимодействия типов .NET](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
