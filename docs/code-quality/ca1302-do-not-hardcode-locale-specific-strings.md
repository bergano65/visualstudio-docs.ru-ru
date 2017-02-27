---
title: "CA1302: не следует жестко кодировать строки, зависящие от языка | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302: не следует жестко кодировать строки, зависящие от языка
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод использует строковый литерал, представляющий часть пути к некоторым системным папкам.  
  
## Описание правила  
 Перечисление <xref:System.Environment.SpecialFolder?displayProperty=fullName> содержит члены, ссылающиеся на определенные системные папки.  Расположение этих папок может различаться в разных ОС, пользователь может менять расположение этих папок, их имена могут быть локализованы.  Примером специальной папки является системная папка; это папка "C:\\WINDOWS\\system32" в [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] или папка "C:\\WINNT\\system32" в [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)].  Метод <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> возвращает расположения, связанные с перечислением <xref:System.Environment.SpecialFolder>.  Расположения, возвращенные методом <xref:System.Environment.GetFolderPath%2A>, локализованы и соответствуют компьютеру, на котором в данный момент выполняется программа.  
  
 Это правило разделяет пути к папкам, извлеченные с помощью метода <xref:System.Environment.GetFolderPath%2A>, на отдельные уровни каталогов.  Каждый строковый литерал сравнивается с маркерами.  При совпадении предполагается, что метод создает строку, ссылающуюся на системное расположение, связанное с маркером.  В целях обеспечения переносимости программ и возможности их локализации используйте метод <xref:System.Environment.GetFolderPath%2A> для извлечения расположений системных папок вместо использования строковых литералов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, извлеките расположение с помощью метода <xref:System.Environment.GetFolderPath%2A>.  
  
## Отключение предупреждений  
 Можно безопасно отключать предупреждения этого правила, если строковый литерал не используется для ссылки на одну из системных папок, связанных с перечислением <xref:System.Environment.SpecialFolder>.  
  
## Пример  
 В следующем примере строится путь к общей папке приложений, и правило выдает три предупреждения.  Затем программа извлекает путь с помощью метода <xref:System.Environment.GetFolderPath%2A>.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Связанные правила  
 [CA1303: не следует передавать литералы в виде локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)