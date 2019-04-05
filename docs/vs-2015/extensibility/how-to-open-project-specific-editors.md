---
title: Практическое руководство. Открытие редакторов соответствующих проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbafb5938f26b4cdb702168ee2f3500def7ac9c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992814"
---
# <a name="how-to-open-project-specific-editors"></a>Практическое руководство. Открытие редакторов соответствующих проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если файл элемента, открываемый в проекте по своей природе привязана к конкретного редактора для этого проекта, проект необходимо открыть файл с помощью редактора определенного проекта. Файл не может быть делегирована вниз, чтобы механизм IDE для выбора редактора. Например вместо того чтобы использовать редактор стандартных растрового изображения, можно использовать этот параметр, редактор для конкретного проекта для указания в редакторе определенного точечного рисунка, который распознает сведения в файле, который является уникальным для проекта.  
  
 Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод, если класс определит, что файл следует открывать с конкретного проекта. Дополнительные сведения см. в разделе [отображение файлов с помощью команды откройте файл](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Следуйте приведенным ниже рекомендациям для реализации `OpenItem` методу иметь проекта откройте файл с помощью редактора определенного проекта.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Чтобы реализовать метод OpenItem с помощью редактора для конкретного проекта  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> метод (RDT_EditLock), чтобы определить, является ли файл (объект данных документа) уже открыт.  
  
    > [!NOTE]
    >  Дополнительные сведения о данных документа и объекты представления документа, см. в разделе [данные документа и представление документа в редакторах Custom](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Если файл уже открыт, resurface файл путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод и указав значение ido_activateifopen для `grfIDO` параметра.  
  
     Если файл открыт и принадлежит проект, отличный от вызывающего проекта документа, предупреждение отображается для пользователя, открывается редактор из другого проекта. Затем отображается окно файла.  
  
3.  Если ваш текстовый буфер (объект данных документа) уже открыт и вы хотите назначить другое представление, вы несете ответственность для привязки этого представления. Рекомендуемый подход для создания представления (объекта представления документа) из проекта, выглядит следующим образом:  
  
    1.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> службу, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> интерфейс.  
  
    2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> метод для создания экземпляра класса представления документа.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод, указывая объекте представления документа.  
  
     Этот метод узлы объекта представления документа в окне документа.  
  
5.  Выполните соответствующие вызовы либо <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> методы.  
  
     На этом этапе представление должно быть полностью инициализирована и готова для открытия.  
  
6.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метод для отображения и откройте представление.  
  
## <a name="see-also"></a>См. также  
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Практическое руководство. Стандартные редакторы](../extensibility/how-to-open-standard-editors.md)   
 [Практическое руководство. Открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
