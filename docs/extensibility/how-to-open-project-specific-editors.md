---
title: 'Как: Открыть проект-специфические редакторы (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710842"
---
# <a name="how-to-open-project-specific-editors"></a>Как: Открыть редакторы для конкретных проектов
Если файл элемента, открываемый проектом, неразрывно связан с конкретным редактором этого проекта, проект должен открыть файл с помощью редактора, конкретного проекта. Файл не может быть делегирован механизму IDE для выбора редактора. Например, вместо использования стандартного редактора bitmap можно использовать этот вариант редактора для конкретного проекта, чтобы указать конкретный редактор битовой карты, который распознает информацию в файле, который является уникальным для вашего проекта.

 IDE вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод, когда он определяет, что файл должен быть открыт конкретным проектом. Для получения дополнительной информации [см. Файлы Display с помощью команды Open File.](../extensibility/internals/displaying-files-by-using-the-open-file-command.md) Используйте следующие рекомендации `OpenItem` для реализации метода, чтобы ваш проект открыл файл с помощью редактора, конкретного проекта.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Реализация метода OpenItem с редактором, специфичным для проекта

1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> `RDT_EditLock`метод (), чтобы определить, является ли файл (объект данных документа) уже открытым.

    > [!NOTE]
    > Для получения дополнительной информации о данных документов и объектах представления документов смотрите [данные документа и представление документов в пользовательских редакторах.](../extensibility/document-data-and-document-view-in-custom-editors.md)

2. Если файл уже открыт, покройте файл, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> позвонив по методу `grfIDO` и указав значение IDO_ActivateIfOpen для параметра.

     Если файл открыт и документ принадлежит проекту, не являющимся проектом вызова, пользователю будет отображаться предупреждение о том, что открываемый редактор — от другого проекта. Затем всплывает окно файла.

3. Если буфер текста (объект данных документа) уже открыт и вы хотите прикрепить к нему другое представление, вы несете ответственность за подключение этого представления. Рекомендуемый подход к мгновенному представлению (объекту представления документа) из проекта следующий:

    1. Позвоните `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> в службу, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> получить указатель на интерфейс.

    2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> метод для создания экземпляра класса представления документа.

4. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод, указав объект представления документа.

     Этот метод успоняет объект представления документа в окне документа.

5. Выполните соответствующие вызовы либо к методам, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> либо к <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> методам.

     На данном этапе мнение должно быть полностью инициализировано и готово к открытию.

6. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> метода, чтобы показать и открыть представление.

## <a name="see-also"></a>См. также
- [Открыть и сохранить элементы проекта](../extensibility/internals/opening-and-saving-project-items.md)
- [Как: Открытые стандартные редакторы](../extensibility/how-to-open-standard-editors.md)
- [Как: Открыть редакторы для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)
