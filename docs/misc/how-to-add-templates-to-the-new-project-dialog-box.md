---
title: "Практическое руководство. Добавление шаблонов в диалоговое окно создания проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "диалоговые окна, добавление шаблонов в проект"
  - "проекты [Visual Studio SDK], добавление шаблонов в диалоговое окно"
  - "шаблоны [Visual Studio], добавление в диалоговое окно проекта"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Практическое руководство. Добавление шаблонов в диалоговое окно создания проекта
При установке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливается ряд предопределенных шаблонов проектов. Полный список предопределенных шаблонов проектов см. в разделе [NIB: создание проектов из шаблонов](http://msdn.microsoft.com/ru-ru/7c36d86a-6b79-4480-8228-0f925f1204b2). Помимо шаблонов проектов по умолчанию можно создать пользовательские шаблоны проектов или шаблоны проектов для определенных подтипов. Например, подтип **Интеллектуальное устройство** предоставляет свои собственные шаблоны для проектов [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Инструкции по созданию пользовательского шаблона см. в разделе [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md).  
  
## Добавление шаблона в диалоговое окно создания проекта  
  
#### Добавление шаблона в диалоговое окно создания проекта  
  
1.  Создайте шаблон, включая файл MyTemplate.vstemplate.  
  
2.  Выберите в этом шаблоне файлы \(включая VSTEMPLATE\-файл\), щелкните их правой кнопкой мыши, выберите пункт **Отправить**, а затем выберите **Сжатая ZIP\-папка**. Выбранные файлы будут сжаты в ZIP\-файл.  
  
 Поместите ZIP\-файл шаблона в папку **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates**.  
  
## См. также  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB: шаблоны Visual Studio](http://msdn.microsoft.com/ru-ru/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Способствовали добавить новый элемент\-диалоговое окно](../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)