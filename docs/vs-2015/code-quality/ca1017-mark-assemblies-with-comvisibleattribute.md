---
title: CA1017. Помечайте сборки атрибутом ComVisibleAttribute | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1a5adc7e9fcb0ee78a7dd93f05209ea331d3c768
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991625"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017. Пометьте сборки с помощью ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибут, примененный к нему.

## <a name="rule-description"></a>Описание правила
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Атрибут определяет, как COM-клиентам доступ к управляемому коду. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM можно задать для всей сборки и затем переопределить ее для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки будет видимым COM-клиентам.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке. Если вы не хотите, чтобы сборка должна быть видимыми для COM-клиентам, примените атрибут и присвойте ему значение `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если требуется сборка должна быть видимой, примените атрибут и присвойте ему значение `true`.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут, примененный к запрещающий видимыми для COM-клиентам.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [уточнение типов .NET для взаимодействия](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
