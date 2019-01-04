---
title: Определение того, какой редактор открывает файл в проекте | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61aa726a7088d08db6d759a9835816dcaf826a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941064"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Определить, какой редактор открывает файл в проект
Когда пользователь открывает файл в проект, среда переходит в процессе опроса, со временем открыть соответствующий редактор или конструктор для этого файла. Начальной процедуру, чтобы позволить среде одинаков для стандартных и пользовательских редакторов. В среде используется различных критериев, при опросе с целью какой редактор для открытия файла и VSPackage необходимо согласовать со средой во время этого процесса.  
  
 Например, когда пользователь выбирает **откройте** команду **файл** меню, а затем нажмет *filename.rtf* (или любой другой файл с *.rtf*расширения), среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> реализации для каждого проекта, в конечном итоге перебирать все экземпляры проекта в решении. Проекты возвращают набор флагов, определяющих утверждений в документе по приоритету. С помощью самым высоким приоритетом, среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Дополнительные сведения о процессе опроса, см. в разделе [добавить проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Проект прочих файлов утверждений все файлы, которые не полученное в других проектах. Таким образом, пользовательских редакторов можно открывать документы, прежде чем стандартные редакторы открыть их. Если проект прочих файлов утверждений файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы открыть файл с помощью стандартного редактора. Среда проверяет свой внутренний список зарегистрированных редакторы для, обрабатывающий *.rtf* файлов. Этот список находится в реестре по адресу следующий раздел:  
  
 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<версии > \Editors\\\<идентификатор guid фабрики редакторов > \Extensions**
  
 Среда также проверяет идентификаторы класса **HKEY_CLASSES_ROOT\CLSID** ключей для любых объектов, содержащие подраздел **DocObject**. Если обнаруживается расширение файла, встроенную версию приложения, например Microsoft Word создается на месте в Visual Studio. Эти объекты документа должен быть составные файлы, которые реализуют <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> необходимо реализовать интерфейс, либо этого объекта <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс.  
  
 Если отсутствует фабрика редактора для *.rtf* файлов в реестре, а затем ищет среды **HKEY_CLASSES_ROOT\\.rtf** ключа и откроется редактор, указанные в ней. Если расширение файла не найден в **HKEY_CLASSES_ROOT**, а затем в среде используется базовый текстовый редактор Visual Studio откройте файл, если это текстовый файл.  
  
 В случае сбоя базовый текстовый редактор которого происходит, если файл не является текстовый файл, затем в среде используется его двоичный редактор для файла.  
  
 Если среде удается найти редактор для *.rtf* расширение в свой реестр, загружает пакет VSPackage, который реализует этой фабрикой редактора. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод для нового пакета VSPackage. Вызовы VSPackage `QueryService` для `SID_SVsRegistorEditor`, с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод для регистрации фабрики редактора в среде.  
  
 Среды теперь проверяет свой внутренний список зарегистрированных редакторы, чтобы найти фабрику редактора, зарегистрированный для *.rtf* файлов. Среда вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, передавая тип файла имя и представление для создания.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>