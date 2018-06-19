---
title: 'Как: открытие редакторов стандартные | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2adcdc0f2d05061c412c5233a16e21a1b9fb252a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129262"
---
# <a name="how-to-open-standard-editors"></a>Как: открытие редакторов Standard
При открытии стандартного редактора, предоставляется возможность определить стандартного редактора для назначенного типа файлов, вместо указания редактора для конкретного проекта файла интегрированной среды разработки.  
  
 Выполните следующую процедуру для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод. В стандартном редакторе откроется файл проекта.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Чтобы реализовать метод OpenItem с помощью стандартного редактора  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) для определения ли файл объект данных документа уже открыт.  
  
2.  Если файл уже открыт, resurface файл путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод, указывая значение `IDO_ActivateIfOpen` для `grfIDO` параметра.  
  
     Если файл открыт и документ принадлежит другой проект, чем вызывающего проекта, проект получает появится предупреждение о редакторе открываемого из другого проекта. Затем будет отображена окне файла.  
  
3.  Если документ не открыт или не находится в запущенной таблице документов вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод (`OSE_ChooseBestStdEditor`) для открытия стандартного редактора для файла.  
  
     При вызове метода, интегрированная среда разработки выполняет следующие задачи:  
  
    1.  Интегрированной среды разработки сканирует редакторы / {guidEditorType} / расширения раздел реестра, чтобы определить, какие редактор можно открыть файл и имеет наивысший приоритет для выполнения этого.  
  
    2.  После определения редактор можно открыть файл интегрированной среды разработки IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Реализация редактора этот метод возвращает сведения, необходимые для интегрированной среды разработки для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> , а также открытый документ.  
  
    3.  Наконец, интегрированной среды разработки загружает документ в интерфейсе обычные сохраняемости, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Если ранее определено интегрированной среды разработки, иерархия или элемент иерархии был доступен, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> метод для получения контекста на уровне проекта в проекте <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> указатель, чтобы передать их обратно в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> вызова метода.  
  
4.  Вернуть <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> указатель при вызове интегрированной среды разработки IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> для вашего проекта, если вы хотите разрешить контекст получения редактора из проекта.  
  
     Выполнение этого действия позволяет проекта предложение дополнительные службы редактора.  
  
     Если представление документа или объекта представления документа успешно размещенные во фрейме окна, объект инициализируется с его данными путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Как: открытие редакторов конкретного проекта](../extensibility/how-to-open-project-specific-editors.md)   
 [Как: открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Отображение файлов с помощью команды "Открыть файл"](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)