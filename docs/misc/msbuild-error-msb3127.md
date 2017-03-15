---
title: "Ошибка MSBuild MSB3127 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationDefaultIconNotInstalled"
helpviewer_keywords: 
  - "MSB3127"
ms.assetid: 161eea9a-332f-463e-a49e-d4030e937d52
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3127
**MSB3127. Не удается найти значок по умолчанию \<имя значка\> в ссылках текущего файла или он не входит в требуемую группу загрузки.  В имени файла значка по умолчанию учитывается регистр, поэтому имя файла, на который ссылается манифест приложения, должно полностью совпадать с именем файла значка.**  
  
 При публикации приложения, настроенного для использования сопоставления файлов, значок по умолчанию, на который ссылается манифест, должен находиться в ссылках текущего файла или входить в требуемую группу загрузки.  Значок по умолчанию — это значок, который появляется для файлов, имеющих настроенное сопоставление файла \(настроенное расширение имени файла\).  
  
### Чтобы исправить эту ошибку  
  
-   Добавьте в текущий проект файл значка и включите его в требуемую группу загрузки.  Дополнительные сведения см. в разделе [Практическое руководство. Задание файлов, публикуемых с помощью ClickOnce](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md).  
  
## См. также  
 [Страница публикации в конструкторе проектов](../ide/reference/publish-page-project-designer.md)