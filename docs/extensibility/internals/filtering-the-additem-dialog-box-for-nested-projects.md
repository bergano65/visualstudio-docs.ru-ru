---
title: Фильтрация диалогового окна AddItem для вложенных проектов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61a51c69857f9bd8f5b2ad84448b0170b809c18a
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497083"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Фильтрация диалогового окна AddItem для вложенных проектов
При отображении **AddItem** диалоговое окно для вложенного проекта в родительский проект можно контролировать, какие элементы отображаются в диалоговом окне.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Интерфейс позволяет фильтровать узлы, которые будут находиться в **AddItem** диалоговое окно. При отображении дочернему проекту **AddItem** диалоговом окне можно реализовать родительского `IVsFilterAddProjectItemDlg` интерфейс и фильтрация элементов, которые могут отображаться в проекте дочернего элемента.  
  
 Если проекты сгруппированы по функциям конкретного родительского проектов, вы можете реализовать `IVsFilterAddProjectItemDlg` при выборе пользователем **добавить элемент проекта** в контекстном меню во вложенном проекте. Реализация `IvsFilterAddProjectItemDlg displays` только проект элементы или файлы, относящиеся к этой группе. Элементы проекта для других групп, исключаются из диалоговом окне, даже если они хранятся в том же каталоге.  
  
 Когда пользователь открывает **AddItem** диалоговое окно для дочернего элемента, родительский проект реализация `IVsFilterAddProjectItemDlg` интерфейс называется.  
  
 `IVsFilterAddProjectItemDlg` Интерфейса также можно реализовать фильтрацию по категории. Дополнительные сведения см. в разделе [Добавление элементов в диалоговом окне Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Добавление элементов в диалоговом окне Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)