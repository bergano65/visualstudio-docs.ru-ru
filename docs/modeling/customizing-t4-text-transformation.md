---
title: "Customizing T4 Text Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, API"
  - "text templates, custom hosts"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
caps.handback.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Customizing T4 Text Transformation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Поддержка текстовых шаблонов – это функция [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], позволяющая генерировать программный или другие текстовые файлы посредством процесса преобразования.  Используя [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], можно расширить используемый по умолчанию процесс преобразования шаблона, настроив процессор директив текстового шаблона или основное приложение текстового шаблона.  
  
## В этом подразделе  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Описано, как работает текстовое преобразование и какова роль основного приложения шаблона и процессоров директив.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Процессор директив обрабатывает содержащиеся в шаблоне директивы, такие как директива `<#@template#>.` Он выполняется в процессе компиляции шаблона и может загружать сборки и другие ресурсы.  Также он может вставлять код, загружающий ресурсы во время выполнения.  Определив собственный процессор директив, можно уменьшить сложность шаблонов.  
  
 [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 При создании расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такого как команда меню или обработчик событий, расширение может использовать службу текстовых шаблонов для преобразования любого текстового шаблона.  Данные параметров можно передать в шаблон, воспользовавшись объектом "Сеанс", и получить значения из шаблона, воспользовавшись директивой `<#@parameter#>`.  
  
 [Processing Text Templates by using a Custom Host](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 При выполнении кода текстового шаблона основное приложение предоставляет доступ ко внешним файлам и состоянию приложения.  Например, основное приложение, выполняющее преобразование текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], может предоставлять доступ к обозревателю решений.  Также оно отображает окно с сообщениями об ошибках.  Если требуется выполнить преобразования текста в другом контексте, можно определить собственное основное приложение, представляющее доступ к доступным в этом контексте службам.  
  
 При создании расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно воспользоваться имеющейся службой преобразования текста, а не создавать собственный узел.  Дополнительные сведения см. в разделе [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Ссылка  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директив текстового шаблона и управляющие блоки.