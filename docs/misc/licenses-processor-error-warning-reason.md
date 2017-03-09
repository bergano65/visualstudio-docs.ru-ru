---
title: "Licenses processor error/warning: &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_task"
ms.assetid: 85750198-7bd3-4936-b1eb-954dcc3ff573
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Licenses processor error/warning: &lt;reason&gt;
Это сообщение об ошибке или предупреждение выводится на экран, если обработчик лицензий возвращает ошибку или предупреждение при обработке LICX\-файла.  В процессе построения система работы с проектами преобразует файл Licenses.licx \(если таковой имеется\) в двоичный файл для диспетчера лицензий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Это преобразование осуществляется с использованием средств, выполняемых в адресном пространстве основного процесса.  
  
 Наиболее вероятной причиной такого сообщения об ошибке или предупреждения является неверный LICX\-файл.  LICX\-файл может быть поврежден, если он редактировался в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с использованием текстового редактора либо вообще за рамками [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Такие файлы обычно обслуживаются конструкторами Windows Forms и Web Forms.  
  
### Чтобы исправить эту ошибку  
  
1.  Исправьте формат LICX\-файла.  
  
     Сообщение об ошибке означает, что двоичный файл не был создан и процесс построения завершится неудачей.  Предупреждения носят чисто информационный характер.  
  
## См. также  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/ru-ru/f793852c-da06-4d52-a826-65f635844772)