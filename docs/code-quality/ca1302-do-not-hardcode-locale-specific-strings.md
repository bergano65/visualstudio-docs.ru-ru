---
title: "CA1302: Не следует жестко кодировать строки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9fc94331b95f70f5ee73eae24172f1930d0ab8bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: не следует жестко кодировать строки, зависящие от языка
|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод использует строковый литерал, представляющий часть пути к некоторым системным папкам.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Перечисление содержит члены, ссылающиеся на специальные системные папки. Расположение этих папок может иметь различные значения в разных ОС, пользователь может изменить некоторые из расположений и локализованы. Примером особая папка является системной папке, которая является «C:\WINDOWS\system32» на [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , но «C:\WINNT\system32» на [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Метод возвращает расположения, которые связаны с <xref:System.Environment.SpecialFolder> перечисления. Расположения, возвращенных <xref:System.Environment.GetFolderPath%2A> локализуются и подходит для текущего компьютера.  
  
 Это правило размечает пути к папкам, которые извлекаются с помощью <xref:System.Environment.GetFolderPath%2A> метод в отдельный каталог уровни. Каждый строковый литерал сравнивается с токены. Если найдено совпадение, предполагается, что метод создает строку, ссылающийся на системы, связанный с маркером. Для обеспечения переносимости и локализуемость используйте <xref:System.Environment.GetFolderPath%2A> метод для получения расположения специальные системные папки вместо строковых литералов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, получения расположения с помощью <xref:System.Environment.GetFolderPath%2A> метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если строковый литерал не используется для ссылки на одну из системных папок, с которыми связана <xref:System.Environment.SpecialFolder> перечисления.  
  
## <a name="example"></a>Пример  
 Следующий пример строится путь к общей папке приложений, выдает три предупреждения из этого правила. Затем в примере извлекается путь с помощью <xref:System.Environment.GetFolderPath%2A> метод.  
  
 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1303: не следует передавать литералы в виде локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)