---
title: Обработка команд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4198cf6bbed2d8f6172872e4f98f1edb4749e7d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926324"
---
# <a name="command-handling"></a>Обработка команд
В редакторе можно определить новые команды. Команды обычно отображаются в меню, на панели инструментов или в контекстном меню.  
  
 Дополнительные сведения об определении команды и меню, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Языковая служба можно контролировать, какие контекстные меню отображаются в редакторе, перехватывая <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления. Кроме того можно управлять отдельно для каждого маркера в контекстном меню. Дополнительные сведения см. в разделе [важные команды для фильтров языковой службы](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="add-commands-to-the-editor-context-menu"></a>Добавление команд в контекстное меню редактора  
 Добавление команды в контекстное меню, необходимо сначала определить набор команд меню, принадлежащих к определенной группе. Следующий пример взят из *.vsct* файл, созданный в ходе этого пошагового руководства [Пошаговое руководство: Добавление компонентов в специализированный редактор](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Guid меню = «guidCustomEditorCmdSet» id = «IDMX_RTF» priority = «0x0000» type = «Контекст» >  
  
 \<Идентификатор guid родительского = «guidCustomEditorCmdSet» id = «0» / >  
  
 \<Строки >  
  
 \<ButtonText > CustomEditor контекстное меню\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Строки >  
  
 \</ Меню >  
  
 \</ Меню >  
  
 Текст выше добавляет команды контекстного меню с текстом **CustomEditor контекстное меню**. Идентификатор GUID меню является частью набора команд, которая создается с этим редактором. Тип — «Контекст».  
  
 Также можно использовать стандартные команды, которые не должны быть определены в *.vsct* файла. Например, проверить *EditorPane.cs* файл, созданный с помощью шаблона пакета Visual Studio. Вы увидите, что набор стандартных команд, таких как <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> определяется <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, обрабатываются в обработчиков команд, таких как `onSelectAll` метод.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)