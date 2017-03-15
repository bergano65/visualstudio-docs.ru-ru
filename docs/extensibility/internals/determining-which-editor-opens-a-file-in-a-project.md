---
title: "Определение того, какой редактор открывает файл в проект | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Определение редактора откроется файл в проекте
При открытии файла в проекте среды проходит процесс опроса, в конечном счете открыть соответствующий редактор или конструктор для этого файла. Начальный используемой среде одинакова для стандартных и пользовательских редакторов. В среде используются различные условия при опросе редактор для открытия файла и VSPackage необходимо координировать со средой во время этого процесса.  
  
 Например, когда пользователь выбирает **откройте** из **файл** меню и затем выбирает `filename`.rtf (или любой другой файл с расширением .rtf), среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>реализацию для каждого проекта, в конечном счете перебирать все экземпляры проекта в решении.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Проекты возвращают набор флагов, определяющих утверждения документа по приоритету. С помощью наивысший приоритет, среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Дополнительные сведения о процессе опроса [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Проект прочих файлов утверждений все файлы, которые не требуются в других проектах. Таким образом, пользовательских редакторов можно открывать документы, прежде чем стандартные редакторы открыть их. Если проект прочих файлов утверждений файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>метод, чтобы открыть файл с помощью стандартного редактора.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Среда проверяет свой внутренний список зарегистрированных редакторов ту, которая обрабатывает RTF-файлы. Этот список находится в в следующий раздел реестра:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`настроек \Editors\\{`editor factory guid`настроек} \Extensions]  
  
 Среду также проверяет идентификаторы класса в ключе HKEY_CLASSES_ROOT\CLSID для объектов, имеющих подраздел DocObject. Если расширение обнаруживается, встроенной версии приложения, например Microsoft Word создается на месте в Visual Studio. Эти объекты документа должен быть составные файлы, которые реализуют <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>должны реализовывать интерфейс или объект <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 Если нет фабрика редактора для RTF-файлы в реестре, то среды выглядит в разделе HKEY_CLASSES_ROOT \\ключ .rtf и открывает редактор указанный там. Если расширение файла не найден в разделе HKEY_CLASSES_ROOT, в среде используется текстовый редактор Visual Studio core для открытия файла, если он представляет собой текстовый файл.  
  
 В случае сбоя основной текстовый редактор которого происходит, если файл не является текстовым файлом, затем в среде используется его двоичный редактор для файла.  
  
 Если среде найти редактор для расширения .rtf в его реестр, загружает VSPackage, который реализует этот редактор фабрики. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>метод на новый VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Вызовы VSPackage `QueryService` для `SID_SVsRegistorEditor`, с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>метод для регистрации фабрики редактора в среде.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 Теперь среды повторно проверяет свой внутренний список зарегистрированных редакторы найти фабрику зарегистрированный редактор для RTF-файлы. Среда вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, передавая файл имя и представление создаваемого типа.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
