---
title: "Resources processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.resx_generator_task"
ms.assetid: eb9a1bd0-7e63-4a2b-ad37-54f6e67d9b5a
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources processor error/warning: &lt;reason&gt;
Это сообщение об ошибке или предупреждение выводится на экран, если обработчик лицензий возвращает ошибку или предупреждение при обработке RESX\-файла.  В процессе построения система работы с проектами преобразует каждый RESX\-файл в двоичный файл, распознаваемый диспетчером ресурсов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Это преобразование осуществляется с использованием средств, выполняемых в адресном пространстве основного процесса.  
  
 Наиболее вероятной причиной такой ошибки или предупреждения является неверный RESX\-файл.  RESX\-файл может быть поврежден, если он редактировался в Visual Studio с использованием текстового редактора либо вообще за рамками Visual Studio.  
  
 Такие файлы обычно обслуживаются конструкторами Windows Forms и Web Forms.  
  
### Чтобы исправить эту ошибку  
  
1.  Исправьте формат RESX\-файла.  
  
     Сообщение об ошибке означает, что двоичный файл не был создан и процесс построения завершится неудачей.  Предупреждения носят чисто информационный характер.  
  
## См. также  
 [Resources in .Resx File Format](http://msdn.microsoft.com/ru-ru/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)