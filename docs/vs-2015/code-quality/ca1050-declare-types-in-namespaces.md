---
title: 'CA1050: Объявляйте типы в пространствах имен | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: acc8e574c94bf5b9e5d58899526b1b791006cd30
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878600"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: объявляйте типы в пространствах имен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип определен вне области именованного пространства имен.

## <a name="rule-description"></a>Описание правила
 Типы объявляются в пространствах имен во избежание конфликтов имен и с целью упорядочения связанных типов в иерархии объектов. Типы, которые находятся за пределами любого именованного пространства имен находятся в глобальном пространстве имен, нельзя ссылаться в коде.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, поместите тип в пространстве имен.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Несмотря на то, что вы не отключайте предупреждение из этого правила, можно безопасно использовать, когда сборки не будут использоваться вместе с другими сборками.

## <a name="example"></a>Пример
 Следующий пример показывает это библиотека, которая имеет тип объявлен вне пространства имен и типом, который имеет то же имя, объявленные в пространстве имен.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Пример
 Следующее приложение использует библиотеку, который был определен ранее. Обратите внимание, что тип, объявивший вне пространства имен создается при имя `Test` не указано пространство имен. Обратите внимание, что для доступа к `Test` введите `Goodspace`, требуется указать имя пространства имен.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]



