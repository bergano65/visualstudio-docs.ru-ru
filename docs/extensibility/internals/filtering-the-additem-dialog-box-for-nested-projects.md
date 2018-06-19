---
title: Фильтрация AddItem диалоговым окном для вложенных проектов | Документы Microsoft
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
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128862"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Фильтрация AddItem диалоговым окном для вложенных проектов
При отображении **AddItem** диалоговое окно для вложенного проекта родительский проект можно контролировать набор элементов, отображаемых в диалоговом окне.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Интерфейс позволяет фильтруют узлы, которые будут находиться в **AddItem** диалоговое окно. При отображении к дочернему проекту **AddItem** диалоговое окно, можно реализовать родительский `IVsFilterAddProjectItemDlg` элементы интерфейса и фильтра, которые могут отображаться в проекте значение дочернего элемента.  
  
 Если проекты сгруппированы по функциям в указанной родительской projects, может реализовать `IVsFilterAddProjectItemDlg` при выборе пользователем **добавить элемент проекта** контекстного меню вложенный проект. Реализация `IvsFilterAddProjectItemDlg displays` только проект элементы или файлы, относящиеся к этой группе. Элемент проекта для других групп, исключаются из диалогового окна, даже если они хранятся в том же каталоге.  
  
 Когда пользователь открывает **AddItem** диалоговое окно для дочернего элемента, реализация родительский проект `IVsFilterAddProjectItemDlg` интерфейс называется.  
  
 `IVsFilterAddProjectItemDlg` Интерфейс может также реализовать фильтрацию по категориям. Дополнительные сведения см. в разделе [элементов диалоговые окна добавления нового элемента, добавление](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) и [регистрация проекта и шаблонов элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Проекты вложения](../../extensibility/internals/nesting-projects.md)