---
title: "Определение редактор открывает файл в проекте | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc0105b56f0a33a86953c95e3d36f5d7f00bcd37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Определение редактора откроется файл в проекте
При открытии файла в проекте среда переходит в процессе опроса, в конечном итоге открыть соответствующий редактор или конструктор для этого файла. Для стандартных и пользовательских редакторов начальной процедуры, используемые средой одинаково. В среде используются различные критерии при опросе редактор для открытия файла и VSPackage необходимо координировать со средой во время этого процесса.  
  
 Например, когда пользователь выбирает **откройте** из **файл** меню и затем выбирает `filename`.rtf (или любой другой файл с расширением .rtf), среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Реализация для каждого проекта, в конечном итоге перебирать все экземпляры проекта в решении. Проекты возвращают набор флагов, определяющих утверждений в документе по приоритету. С помощью самый высокий приоритет, среда вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. Дополнительные сведения о процессе опроса [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Прочие файлы проекта утверждений все файлы, которые не требуются в других проектах. Таким образом, пользовательских редакторов можно открывать документы, прежде чем открыть стандартные редакторы их. Если проекта прочих файлов утверждений файл, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы открыть файл с помощью стандартного редактора. Среда проверяет свой внутренний список зарегистрированных редакторы ту, которая обрабатывает RTF-файлы. Этот список находится в в следующий раздел реестра:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Среда также проверяет идентификаторы класса в ключе HKEY_CLASSES_ROOT\CLSID для любых объектов, имеющих подпараметр DocObject. Если обнаруживается расширение файла, встроенной версии приложения, например Microsoft Word, будет создан на месте в Visual Studio. Эти объекты документа должен быть составные файлы, которые реализуют <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> должен реализовывать интерфейс или объект <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> интерфейса.  
  
 Если отсутствует фабрика редактора для RTF-файлы в реестре, а затем ищет среды в раздел HKEY_CLASSES_ROOT \\.rtf ключ и открывает редактор указанный существует. Если расширение файла не найден в раздел HKEY_CLASSES_ROOT, в среде используется текстовый редактор основных компонентов Visual Studio откройте файл, если он является текстовым файлом.  
  
 Если происходит сбой основной текстовый редактор, который происходит, если файл не является текстовый файл, затем в среде используется его двоичный редактор для файла.  
  
 Если среде найти редактор для расширения .rtf в его реестра, он загружает пакет VSPackage, реализующий этот редактор фабрики. Среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод для нового пакета VSPackage. Вызовы VSPackage `QueryService` для `SID_SVsRegistorEditor`, с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метода для регистрации фабрики редакторов в среде.  
  
 Теперь среда повторно проверяет свой внутренний список зарегистрированных редакторы для поиска фабрики редакторов вновь зарегистрированного RTF-файлы. Среда вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, передавая имя и представление тип файла для создания.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>