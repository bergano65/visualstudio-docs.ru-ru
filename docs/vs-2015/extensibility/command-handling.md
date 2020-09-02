---
title: Обработка команд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184375"
---
# <a name="command-handling"></a>Обработка команд
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор может определять новые команды. Команды обычно отображаются в меню, на панели инструментов или в контекстном меню.  
  
 Дополнительные сведения об определении команд и меню см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Языковая служба может управлять тем, какие контекстные меню отображаются в редакторе, перехватывая <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисление. Кроме того, можно управлять контекстным меню для каждого маркера. Дополнительные сведения см. в разделе [важные команды для фильтров языковой службы](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Добавление команд в контекстное меню редактора  
 Чтобы добавить команду в контекстное меню, необходимо сначала определить набор команд меню, принадлежащих определенной группе. Следующий пример взят из файла. vsct, созданного в составе пошагового [руководства: Добавление компонентов в пользовательский редактор](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Контекстное меню Кустомедитор\</ButtonText>  
  
 \<CommandName>кустомедиторконтекстмену\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Приведенный выше текст добавляет команду контекстного меню с **контекстным меню Text кустомедитор**. GUID меню состоит из набора команд, созданного с помощью этого редактора, и типа «context».  
  
 Можно также использовать предопределенные команды, которые не нужно определять в файле. vsct. Например, при просмотре файла EditorPane.cs, созданного с помощью шаблона пакета Visual Studio, вы обнаружите, что набор предопределенных команд, например, <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> определенных <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , обрабатывается в обработчиках команд, таких как метод онселекталл.  
  
## <a name="see-also"></a>См. также:  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
