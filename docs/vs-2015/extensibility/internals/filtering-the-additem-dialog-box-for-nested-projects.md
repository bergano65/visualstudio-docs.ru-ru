---
title: Фильтрация диалогового окна AddItem для вложенных проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538100"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Фильтрация диалогового окна AddItem для вложенных проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При отображении диалогового окна **AddItem** для вложенного проекта родительский проект может управлять тем, какие элементы отображаются в диалоговом окне.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Интерфейс позволяет фильтровать узлы, которые будут находиться в диалоговом окне **AddItem** . Когда в дочернем проекте отображается диалоговое окно **AddItem** , родительский проект может реализовать `IVsFilterAddProjectItemDlg` интерфейс и фильтровать элементы, которые в противном случае будут отображаться в проекте дочернего проекта.  
  
 Если проекты группируются по функциям в конкретных родительских проектах, можно реализовать, `IVsFilterAddProjectItemDlg` когда пользователь выбирает пункт **Добавить проект** в контекстном меню вложенного проекта. Реализация `IvsFilterAddProjectItemDlg displays` только элементов проекта или файлов, относящихся к этой группе. Элементы проекта для других групп отфильтровываются из диалогового окна, даже если они хранятся в одном и том же каталоге.  
  
 Когда пользователь открывает диалоговое окно **AddItem** для дочернего элемента, вызывается реализация интерфейса для родительского проекта `IVsFilterAddProjectItemDlg` .  
  
 `IVsFilterAddProjectItemDlg`Интерфейс также может реализовывать фильтрацию по категории. Дополнительные сведения см. в разделе [Добавление элементов в диалоговые окна Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Добавление элементов в диалоговые окна "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)
