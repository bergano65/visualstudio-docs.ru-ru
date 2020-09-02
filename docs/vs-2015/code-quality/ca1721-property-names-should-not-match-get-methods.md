---
title: 'CA1721: имена свойств не должны совпадать с именами методов Get | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 77ec48a1164c7065ba5033ef51eb704b8361dc1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544460"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721. Имена свойств не должны совпадать с именами методов get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя открытого или защищенного члена начинается с "Get", а в противном случае совпадает с именем открытого или защищенного свойства. Например, тип, содержащий метод с именем "-Color" и свойство с именем "Color", нарушает это правило.

## <a name="rule-description"></a>Описание правила
 Методы get и Properties должны иметь имена, четко отличающие их функции.

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает время, необходимое для изучения новой библиотеки программного обеспечения, и повышает уверенность клиентов в том, что библиотека была разработана пользователями, обладающими опытом в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените имя так, чтобы оно не совпадало с именем метода с префиксом "Get".

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

> [!NOTE]
> Это предупреждение может быть исключено, если метод Get вызван реализацией интерфейса интерфейс IExtenderProvider.

## <a name="example"></a>Пример
 В следующем примере содержится метод и свойство, нарушающее это правило.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1024. По возможности используйте свойства](../code-quality/ca1024-use-properties-where-appropriate.md)
