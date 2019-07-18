---
title: Определение того, какой редактор открывает файл в проекте | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196758"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Определение редактора, с помощью которого откроется файл в проекте
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда пользователь открывает файл в проект, среда переходит в процессе опроса, со временем открыть соответствующий редактор или конструктор для этого файла. Начальной процедуру, чтобы позволить среде одинаков для стандартных и пользовательских редакторов. В среде используется различных критериев, при опросе с целью какой редактор для открытия файла и VSPackage необходимо согласовать со средой во время этого процесса.  
  
 Например, когда пользователь выбирает **откройте** команду **файл** меню, а затем нажмет `filename`.rtf (или любой другой файл с расширением .rtf), среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Реализация для каждого проекта, в конечном итоге перебирать все экземпляры проекта в решении. Проекты возвращают набор флагов, определяющих утверждений в документе по приоритету. С помощью самым высоким приоритетом, среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Дополнительные сведения о процессе опроса [добавление проектов и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Проект прочих файлов утверждений все файлы, которые не полученное в других проектах. Таким образом, пользовательских редакторов можно открывать документы, прежде чем стандартные редакторы открыть их. Если проект прочих файлов утверждений файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы открыть файл с помощью стандартного редактора. Среда проверяет свой внутренний список зарегистрированных редакторы для, обрабатывающий RTF-файлы. Этот список находится в реестре по адресу следующий раздел:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Среда также проверяет идентификаторы класса в ключе HKEY_CLASSES_ROOT\CLSID для объектов, имеющих подпараметр DocObject. Если обнаруживается расширение файла, встроенную версию приложения, например Microsoft Word создается на месте в Visual Studio. Эти объекты документа должен быть составные файлы, которые реализуют <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> необходимо реализовать интерфейс, либо этого объекта <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс.  
  
 Если отсутствует фабрика редактора для RTF-файлы в реестре, а затем ищет среды в HKEY_CLASSES_ROOT \\.rtf ключ и откроется в редакторе указанный там. Если расширение файла не найден в разделе HKEY_CLASSES_ROOT, в среде используется базовый текстовый редактор Visual Studio откройте файл, если это текстовый файл.  
  
 В случае сбоя базовый текстовый редактор которого происходит, если файл не является текстовый файл, затем в среде используется его двоичный редактор для файла.  
  
 Если среде удается найти редактор для расширения .rtf в свой реестр, он загружает пакет VSPackage, который реализует этой фабрикой редактора. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод для нового пакета VSPackage. Вызовы VSPackage `QueryService` для `SID_SVsRegistorEditor`, с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод для регистрации фабрики редактора в среде.  
  
 Теперь среда повторно проверяет свой внутренний список зарегистрированных редакторы найти фабрику редактора, зарегистрированный для RTF-файлы. Среда вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, передавая тип файла имя и представление для создания.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
