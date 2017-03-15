---
title: "Поддержка мастера для вложенных проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Мастер установки элемента"
  - "вложенные проекты, поддержка мастера"
  - "Мастер проектов"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Поддержка мастера для вложенных проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Интегрированная среда разработки запускает 2 мастера, который родительский проект для вложенных проектов может реализовать:  **Создать проект** мастер и  **Добавить элемент** мастер.  
  
 Если пользователь начинает **Создать проект** мастера, выбрав  **Добавьте в проект** и щелкнуть  **Создать проект** в меню " Файл " или путем выбора  **Добавить** и щелкнув правой кнопкой мыши  **Создать проект** в обозревателе решений работает среда разработки  **AddProject** команда и реализация родительского проекта   **AddProject** команда или получает файл проекта или файл шаблона мастера \(vsz\), который содержит набор параметров контекста.  
  
 Аналогично, реализация родительского проекта AddItem мастеры возвращают файл vsz, имеющего другой набор параметров контекста.  
  
 Дополнительные сведения о мастерах см. [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)"  [Мастер \(. Файл VSZ\)](../../extensibility/internals/wizard-dot-vsz-file.md)и  [Контекстные параметры](../../extensibility/internals/context-parameters.md) .  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Вложенность проектов](../../extensibility/internals/nesting-projects.md)