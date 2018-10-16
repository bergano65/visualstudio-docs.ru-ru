---
title: 'CA1721: имена свойств не должны совпадать с именами методов get'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26f6e23a340ec018f766477f0bdce089a43ca3e4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549681"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: имена свойств не должны совпадать с именами методов get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя открытого или защищенного элемента начинается с «Get» и в противном случае соответствует имени открытого или защищенного свойства. Например типом, который содержит метод с именем «GetColor» и свойство с именем «Цвет» нарушает это правило.

## <a name="rule-description"></a>Описание правила
 Методы get и свойства должны иметь имена, четко различать их функции.

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Эта согласованность, сокращает время, необходимое для изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените имя, чтобы он не соответствует имени метода, который добавляется префикс «Get».

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

> [!NOTE]
> Это предупреждение можно не указывать, если вызвана реализация интерфейса IExtenderProvider метод Get.

## <a name="example"></a>Пример
 В следующем примере содержится метод и свойство, которое нарушает это правило.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)