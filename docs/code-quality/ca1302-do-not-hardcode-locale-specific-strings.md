---
title: CA1302. Не указывайте прямо в коде строки, зависящие от языковых стандартов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 69b6256f2c6ae54467eb21cc17d50119b3c67a9f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235179"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302. Не указывайте прямо в коде строки, зависящие от языковых стандартов

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Метод использует строковый литерал, представляющий часть пути к определенным системным папкам.

## <a name="rule-description"></a>Описание правила
<xref:System.Environment.SpecialFolder?displayProperty=fullName> Перечисление содержит члены, которые ссылаются на специальные системные папки. Расположение этих папок может иметь разные значения в разных операционных системах. пользователь может изменить некоторые расположения, а расположения будут локализованы. Примером особой папки является системная папка, «C:\Windows\System32» [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , но «C:\Winnt\System32» в. [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] Метод возвращает расположения, связанные <xref:System.Environment.SpecialFolder> с перечислением. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Расположения, возвращаемые <xref:System.Environment.GetFolderPath%2A> , локализуются и подходят для текущего компьютера.

Это правило разделяет пути к папкам, полученные с помощью <xref:System.Environment.GetFolderPath%2A> метода, на отдельные уровни каталога. Каждый строковый литерал сравнивается с токенами. Если совпадение найдено, предполагается, что метод создает строку, которая ссылается на Системное расположение, связанное с токеном. Для обеспечения переносимости и возможности локализации <xref:System.Environment.GetFolderPath%2A> используйте метод для получения расположений специальных системных папок вместо использования строковых литералов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, извлеките расположение с помощью <xref:System.Environment.GetFolderPath%2A> метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если строковый литерал не используется для ссылки на одно из системных расположений, связанных с <xref:System.Environment.SpecialFolder> перечислением.

## <a name="example"></a>Пример
В следующем примере создается путь к общей папке Application Data, которая создает три предупреждения из этого правила. Затем в примере извлекается путь с помощью <xref:System.Environment.GetFolderPath%2A> метода.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1303 Не передавайте литералы в качестве локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)