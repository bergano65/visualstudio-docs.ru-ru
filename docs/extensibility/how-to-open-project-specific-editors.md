---
title: "Как: открытие редакторов конкретного проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb60f482edeea1271c0f864fd5b907138e83d103
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-open-project-specific-editors"></a>Как: открытие редакторов конкретного проекта
Если файл элемента, открываемого в проекте само по себе привязан к конкретной редактор для этого проекта, проект необходимо открыть файл с помощью редактора для конкретного проекта. Файл не может быть делегирована до механизм IDE для выбора редактора. Например вместо использования редактора стандартный рисунок, можно использовать этот параметр, редактор для конкретного проекта для указания конкретных растрового изображения редактор, который распознает сведения в файле, который является уникальным для проекта.  
  
 Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод, когда она определяет, что файл должен быть открыт в конкретном проекте. Дополнительные сведения см. в разделе [отображение файлов с помощью команды откройте файл](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Следуйте приведенным ниже рекомендациям для реализации `OpenItem` метода проекте откройте файл с помощью редактора для конкретного проекта.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Чтобы реализовать метод OpenItem с помощью редактора для конкретного проекта  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод (RDT_EditLock), чтобы определить, является ли файл (объект данных документа) уже открыт.  
  
    > [!NOTE]
    >  Дополнительные сведения о данных документа и объекты представления документа см. в разделе [данные документа и представление документа в пользовательских редакторов](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Если файл уже открыт, resurface файл путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод и указав значение IDO_ActivateIfOpen для `grfIDO` параметра.  
  
     Если файл открыт и документ принадлежит проекта, отличные от вызывающего, предупреждение будет отображаться для пользователя, редактор открываемого из другого проекта. Затем будет отображена окне файла.  
  
3.  Если вы хотите назначить другое представление буфера текста (объект данных документа) уже открыт, вы отвечаете подключения этого представления. Рекомендуемый подход для создания представления (объект представления документа) из проекта, выглядит следующим образом:  
  
    1.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> службы, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> интерфейса.  
  
    2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> метод для создания экземпляра класса представления документа.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод, указывая объект представления документа.  
  
     Этот метод узлы объекта представления документа в окне документа.  
  
5.  Выполните соответствующие вызовы либо <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> методы.  
  
     На этом этапе представление должно быть полностью инициализирована и готова для открытия.  
  
6.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для отображения и откройте представление.  
  
## <a name="see-also"></a>См. также  
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Как: открытие редакторов Standard](../extensibility/how-to-open-standard-editors.md)   
 [Практическое руководство. Открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)