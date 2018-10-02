---
title: 'CA1302: Делать не следует жестко кодировать строки | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb11fd69973e5771fe9ad7b412f131e686e609ed
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591735"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: не следует жестко кодировать строки, зависящие от языка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1302: делать не следует жестко кодировать строки](https://docs.microsoft.com/visualstudio/code-quality/ca1302-do-not-hardcode-locale-specific-strings).

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод использует строковый литерал, представляющий часть путь к некоторым системным папкам.

## <a name="rule-description"></a>Описание правила
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Перечисление содержит члены, ссылающиеся на специальные системные папки. Расположение этих папок может иметь разные значения в различных операционных системах, пользователь может изменить некоторые из расположений и локализованы. Примером особая папка, которая является системной папке, который является «C:\WINDOWS\system32» на [!INCLUDE[winxp](../includes/winxp-md.md)] , но «C:\WINNT\system32» на [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Метод возвращает расположения, которые связаны с <xref:System.Environment.SpecialFolder> перечисления. Расположения, которые возвращаются <xref:System.Environment.GetFolderPath%2A> локализуются и подходит для текущего компьютера.

 Это правило размечает пути к папкам, которые извлекаются с помощью <xref:System.Environment.GetFolderPath%2A> метод в отдельном каталоге уровни. Каждый строковый литерал сравнивается с токенами. Если соответствие найдено, предполагается, что метод создает строку, ссылающуюся на расположение в системе, связанный с маркером. Для обеспечения переносимости и возможности локализации, используйте <xref:System.Environment.GetFolderPath%2A> метод для извлечения расположения специальные системные папки вместо строковых литералов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, получения расположения указывается с помощью <xref:System.Environment.GetFolderPath%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если строковый литерал не используется для ссылки на одну из системных папок, связанных с <xref:System.Environment.SpecialFolder> перечисления.

## <a name="example"></a>Пример
 Следующий пример создает путь к общей папке приложений, выдает три предупреждения из этого правила. Затем в примере извлекается путь с помощью <xref:System.Environment.GetFolderPath%2A> метод.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1303: не следует передавать литералы в виде локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)



