---
title: 'CA1050: объявляйте типы в пространствах имен'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5bff984d9ea11ba8fd7f2e42deb5898f04da7d44
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548492"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: объявляйте типы в пространствах имен

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

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Пример
 Следующее приложение использует библиотеку, который был определен ранее. Обратите внимание, что тип, объявивший вне пространства имен создается при имя `Test` не указано пространство имен. Обратите внимание, что для доступа к `Test` введите `Goodspace`, требуется указать имя пространства имен.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]