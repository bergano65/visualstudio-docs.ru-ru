---
title: 'Как: Открытые стандартные редакторы Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710789"
---
# <a name="how-to-open-standard-editors"></a>Как: Открытые стандартные редакторы
При открытии стандартного редактора вы позволяете IDE определять стандартный редактор для определенного типа файлов вместо указания конкретного редактора для файла.

 Выполните следующую процедуру для реализации метода. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Это позволит открыть файл проекта в стандартном редакторе.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Реализация метода OpenItem со стандартным редактором

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Звоните`RDT_EditLock`() чтобы определить, открыт ли файл объектов данных документа.

2. Если файл уже открыт, покройте файл, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> позвонив в `IDO_ActivateIfOpen` метод, указав значение `grfIDO` параметра.

     Если файл открыт и документ принадлежит другому проекту, чем проект вызова, проект получает предупреждение о том, что открываемый редактор принадлежит другому проекту. Затем всплывает окно файла.

3. Если документ не открыт или не находится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> таблице`OSE_ChooseBestStdEditor`подходящего документа, позвоните в метод () — открыть стандартный редактор для файла.

     При вызове метода IDE выполняет следующие задачи:

    1. IDE сканирует редакторы /«guidEditorType»/расширения подключили в реестре, чтобы определить, какой редактор может открыть файл и имеет наивысший приоритет для этого.

    2. После того, как IDE определил, какой редактор <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>может открыть файл, IDE вызывает . Реализация редактором этого метода возвращает информацию, необходимую <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> для вызова IDE и сайта недавно открытого документа.

    3. Наконец, IDE загружает документ, используя обычный <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>интерфейс настойчивости, например.

    4. Если IDE ранее определило, что элемент иерархии или иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> доступен, IDE вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> проекта, чтобы получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> указатель контекста на уровне проекта, чтобы передать обратно с вызовом метода.

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Верните указатель в IDE, когда <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> IDE призывает ваш проект, если вы хотите, чтобы редактор получил контекст из вашего проекта.

     Выполнение этого шага позволяет проекту предлагать дополнительные услуги редактору.

     Если объект представления документа или представления документа был успешно размещен в оконной раме, объект инициализируется с его данными, вызывая <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Откройте и сохраните элементы проекта](../extensibility/internals/opening-and-saving-project-items.md)
- [Как: Открыть редакторы для конкретных проектов](../extensibility/how-to-open-project-specific-editors.md)
- [Как: Открыть редакторы для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
- [Отображение файлов с помощью команды Open File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
