---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
Вспомогательная сборка для указанного языка и региональных параметров не может быть построена.  При возникновении этой ошибки процесс построения завершается неудачей.  
  
 Эта ошибка может возникнуть по двум указанным ниже причинам.  
  
1.  Файл ALINK.EXE не установлен в системе.  
  
2.  При выполнении ALINK.EXE произошел сбой, но расширенные сведения об ошибке возвращены не были.  
  
 **Чтобы исправить эту ошибку**  
  
-   Переустановите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или только [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   Если в строке \<причина\> отображается сообщение: "Не удается запустить компоновщик сборок."  Файл существует", удалите все файлы из папки "Temp", в которой создаются файлы \(например, C:\\Documents and Settings\\\<пользователь\>\\Local Settings\\Temp\).  
  
## См. также  
 [Al.exe \(компоновщик сборок\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)