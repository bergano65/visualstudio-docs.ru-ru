---
title: "Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_write_gen_output"
ms.assetid: eafcee9e-186b-4019-9042-8d8f9fc0925a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to write the output of custom tool &#39;tool&#39; to file &#39;file&#39;. &lt;reason&gt;
Системе работы с проектами не удалось записать выходные данные пользовательского инструмента в указанный файл.  
  
 Если имя файла с исходными данными для пользовательского инструмента не меняется, то имя выходного файла этого средства также остается неизменным.  Эта ошибка происходит, если созданные выходные данные заблокированы на диске.  
  
 **Чтобы исправить эту ошибку**  
  
-   Перезапустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и затем повторно запустите пользовательский инструмент, щелкнув правой кнопкой мыши указанный файл и выбрав команду **Запустить пользовательский инструмент** из контекстного меню.  
  
     Выходной файл, возможно, устарел, потому что система работы с проектами не смогла его обновить.