---
title: Обработка команд | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 542277c5d8ab1b9b130f31bbb06215d8da7bc2ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="command-handling"></a>Обработка команд
В редакторе можно определить новые команды. Обычно в меню, на панели инструментов или в контекстном меню отображаются команды.  
  
 Дополнительные сведения об определении команды и меню см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Служба языка можно контролировать, какие контекстные меню отображаются в редакторе, перехватывая <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления. Кроме того можно управлять отдельно для каждого маркера в контекстном меню. Дополнительные сведения см. [важные команды для фильтров службы языка](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Добавление команд в контекстное меню редактора  
 Добавление команды в контекстное меню, сначала необходимо определить набор команд меню, принадлежащих к определенной группе. Следующий пример взят из файла vsct, в рамках этого пошагового руководства [Пошаговое руководство: Добавление функции специализированного редактора](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Меню guid = «guidCustomEditorCmdSet» id = «IDMX_RTF» приоритет = «0x0000» type = «Контекст» >  
  
 \<Идентификатор guid родительского = «guidCustomEditorCmdSet» id = «0» / >  
  
 \<Строки >  
  
 \<ButtonText > CustomEditor контекстное меню\</ButtonText >  
  
 \<Имя_команды > CustomEditorContextMenu\</CommandName >  
  
 \</ Строки >  
  
 \<-Меню >  
  
 \<-Меню >  
  
 Текст выше добавляет команды контекстного меню с текстом **CustomEditor контекстное меню**. Идентификатор GUID меню — набора команд, созданного в этом редакторе, что тип является «Контекст».  
  
 Можно также использовать стандартные команды, которые не обязательно должны быть определены в vsct-файле. Например, при просмотре файла EditorPane.cs, созданной с помощью шаблона пакета Visual Studio выясниться, что набор стандартных команд, таких как <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> определяется <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, обрабатываются в обработчики команд, например метода onSelectAll.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)