---
title: Обработка команд | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d26350e9b0465b3a175cb135509f85cf69da21f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778817"
---
# <a name="command-handling"></a>Обработка команд
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В редакторе можно определить новые команды. Команды обычно отображаются в меню, на панели инструментов или в контекстном меню.  
  
 Дополнительные сведения об определении команды и меню, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Языковая служба можно контролировать, какие контекстные меню отображаются в редакторе, перехватывая <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления. Кроме того можно управлять отдельно для каждого маркера в контекстном меню. Дополнительные сведения см. в разделе [важные команды для фильтров языковой службы](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Добавление команд в контекстное меню редактора  
 Добавление команды в контекстное меню, необходимо сначала определить набор команд меню, принадлежащих к определенной группе. Следующий пример взят из vsct-файл, созданный в ходе этого пошагового руководства [Пошаговое руководство: добавление функций в специализированный редактор](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid меню = «guidCustomEditorCmdSet» id = «IDMX_RTF» priority = «0x0000» type = «Контекст» >  
  
 \<Идентификатор guid родительского = «guidCustomEditorCmdSet» id = «0» / >  
  
 \<Строки >  
  
 \<ButtonText > CustomEditor контекстное меню\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Строки >  
  
 \</ Меню >  
  
 \</ Меню >  
  
 Текст выше добавляет команды контекстного меню с текстом **CustomEditor контекстное меню**. Идентификатор GUID меню — набора команд, созданный с помощью этого редактора, что тип является «Контекст».  
  
 Также можно использовать стандартные команды, которые не обязательно должны быть определены в vsct-файле. Например, если изучить файл EditorPane.cs, созданный с помощью шаблона пакета Visual Studio, выяснится, что набор стандартных команд, таких как <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> определяется <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, обрабатываются в обработчиков команд, таких как метод onSelectAll.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)

