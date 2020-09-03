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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196758"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Определение редактора, с помощью которого откроется файл в проекте
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Когда пользователь открывает файл в проекте, среда проходит процесс опроса, в конечном итоге открывая соответствующий редактор или конструктор для этого файла. Начальная процедура, применяемая средой, одинакова для стандартных и пользовательских редакторов. При опросе редактора, используемого для открытия файла, среда использует разнообразные критерии, и пакет VSPackage должен координировать среду во время этого процесса.  
  
 Например, когда пользователь выбирает команду **Открыть** в меню **файл** , а затем выбирает `filename` . RTF (или любой другой файл с расширением. RTF), среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> реализацию для каждого проекта, постепенно переключаясь по всем экземплярам проекта в решении. Проекты возвращают набор флагов, которые определяют утверждения для документа по приоритету. При использовании наивысшего приоритета среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Для получения дополнительных сведений о процессе опроса [добавьте шаблоны проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Проект "Прочие файлы" заявляет все файлы, которые не затребованы другими проектами. Таким образом, пользовательские редакторы могут открывать документы до их открытия в стандартных редакторах. Если проект прочих файлов требует файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы открыть файл в стандартном редакторе. Среда проверяет внутренний список зарегистрированных редакторов для одного, обрабатывающего RTF файлы. Этот список находится в реестре в следующем разделе:  
  
 [HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ < `version`> \Едиторс \\ {<`editor factory guid`>} \екстенсионс]  
  
 Среда также проверяет идентификаторы классов в HKEY_CLASSES_ROOTном ключе \КЛСИД для любых объектов, имеющих подключ DocObject. Если расширение файла найдено, на месте в Visual Studio создается внедренная версия приложения, например Microsoft Word. Эти объекты документов должны быть составными файлами, реализующими <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> интерфейс, или объект должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейс.  
  
 Если в реестре нет фабрики редактора для RTF-файлов, среда ищет \\ ключ HKEY_CLASSES_ROOT. RTF и открывает редактор, указанный там. Если расширение файла не найдено в HKEY_CLASSES_ROOT, среда использует текстовый редактор Visual Studio Core для открытия файла, если это текстовый файл.  
  
 Если основной текстовый редактор завершается ошибкой, что происходит, если файл не является текстовым, среда использует двоичный редактор для файла.  
  
 Если среда находит редактор для расширения RTF в своем реестре, он загружает пакет VSPackage, реализующий эту фабрику редактора. Среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод для нового пакета VSPackage. Пакет VSPackage вызывает `QueryService` для `SID_SVsRegistorEditor` , используя <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод для регистрации фабрики редактора в среде.  
  
 Среда теперь повторно проверяет внутренний список зарегистрированных редакторов, чтобы найти только что зарегистрированную фабрику редактора для RTF-файлов. Среда вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода, передавая имя файла и тип представления для создания.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
