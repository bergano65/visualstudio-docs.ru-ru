---
title: 'CA1302: не жестко кодировать строки, специфичные для локали | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661477"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: не следует жестко кодировать строки, зависящие от языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод использует строковый литерал, представляющий часть пути к определенным системным папкам.

## <a name="rule-description"></a>Описание правила
 Перечисление <xref:System.Environment.SpecialFolder?displayProperty=fullName> содержит элементы, которые ссылаются на специальные системные папки. Расположение этих папок может иметь разные значения в разных операционных системах. пользователь может изменить некоторые расположения, а расположения будут локализованы. Примером особой папки является системная папка, «C:\WINDOWS\system32» на [!INCLUDE[winxp](../includes/winxp-md.md)], но «C:\WINNT\system32» на [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. Метод <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Возвращает расположения, связанные с перечислением <xref:System.Environment.SpecialFolder>. Расположения, возвращаемые <xref:System.Environment.GetFolderPath%2A>, локализуются и подходят для текущего компьютера.

 Это правило разделяет пути к папкам, полученные с помощью метода <xref:System.Environment.GetFolderPath%2A>, на отдельные уровни каталога. Каждый строковый литерал сравнивается с токенами. Если совпадение найдено, предполагается, что метод создает строку, которая ссылается на Системное расположение, связанное с токеном. Для обеспечения переносимости и возможности локализации используйте метод <xref:System.Environment.GetFolderPath%2A>, чтобы извлечь расположения специальных системных папок вместо использования строковых литералов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, извлеките расположение с помощью метода <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если строковый литерал не используется для ссылки на одно из системных расположений, связанных с перечислением <xref:System.Environment.SpecialFolder>.

## <a name="example"></a>Пример
 В следующем примере создается путь к общей папке Application Data, которая создает три предупреждения из этого правила. Далее пример извлекает путь с помощью метода <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1303: не следует передавать литералы в виде локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
