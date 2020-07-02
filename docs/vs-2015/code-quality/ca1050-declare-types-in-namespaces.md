---
title: 'CA1050: объявление типов в пространствах имен | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0a4dcc53fac7dc9b7e189686a3b32e2fb4fd030
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539598"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050. Объявите типы в пространствах имен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип определен вне области именованного пространства имен.

## <a name="rule-description"></a>Описание правила
 Типы объявляются в пространствах имен для предотвращения конфликтов имен, а также как способ организации связанных типов в иерархии объектов. Типы, находящиеся за пределами именованного пространства имен, находятся в глобальном пространстве имен, на которое нельзя ссылаться в коде.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, разместите тип в пространстве имен.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Несмотря на то, что не нужно отключать предупреждение из этого правила, это можно сделать в том случае, если сборка никогда не будет использоваться вместе с другими сборками.

## <a name="example"></a>Пример
 В следующем примере показана библиотека с типом, неверно объявленным вне пространства имен, и типом с тем же именем, объявленным в пространстве имен.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Пример
 В следующем приложении используется библиотека, определенная ранее. Обратите внимание, что тип, объявленный вне пространства имен, создается, когда имя `Test` не уточняется пространством имен. Обратите внимание, что для доступа к `Test` типу в необходимо `Goodspace` указать имя пространства имен.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
