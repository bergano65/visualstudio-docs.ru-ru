---
title: "Обработка команд | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - обработка команд"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Обработка команд
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редактор можно определить новые команды. Обычно команды отображаются в меню, на панели инструментов или в контекстном меню.  
  
 Дополнительные сведения об определении команды и меню см. в разделе [команд, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Служба языка можно контролировать, какие контекстные меню отображаются в редакторе, перехватывая <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления. Кроме того можно управлять отдельно для каждого маркера в контекстном меню. Дополнительные сведения см. [важные команды языка службы фильтров](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Добавление команд в контекстное меню редактора  
 Добавление команды в контекстное меню, необходимо сначала определить набор команд меню, принадлежащих к определенной группе. Следующий пример взят из файла .vsct, созданные в рамках данного пошагового руководства [Пошаговое руководство: Добавление функции пользовательского редактора](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< guid меню = идентификатор «guidCustomEditorCmdSet» = «IDMX_RTF» приоритет = тип «0x0000» = «Контекст»>  
  
 \< guid родительского = идентификатор «guidCustomEditorCmdSet» = «0» или>  
  
 \< строк>  
  
 \< ButtonText>CustomEditor контекстное меню \< / ButtonText>  
  
 \< CommandName>CustomEditorContextMenu \< / CommandName>  
  
 \< / строки>  
  
 \<-меню>  
  
 \<-меню>  
  
 Добавляет текст выше командой контекстного меню с текстом **CustomEditor контекстное меню**. Идентификатор GUID меню — набора команд, созданную с помощью этого редактора, что тип является «Контекст».  
  
 Можно также использовать стандартные команды, которые не обязательно должны быть определены в файле .vsct. Например, при просмотре файла EditorPane.cs, созданной с помощью шаблона пакета Visual Studio замечено, что набор стандартных команд, таких как <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> определяется <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, обрабатываются в обработчиков команд, таких как метод onSelectAll.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)