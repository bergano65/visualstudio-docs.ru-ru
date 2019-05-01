---
title: Фабрики редакторов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5c6b6dc6f02bfc22e6a02f708deefe4208d91ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912634"
---
# <a name="editor-factories"></a>Фабрики редакторов
Фабрику редактора создает объекты редактор и помещает их в рамку окна, известный как физическое представление. Он создает данные документа и объекты представления документа, которые необходимы для создания в редакторах и конструкторах. Фабрику редактора необходима для создания базового редактора Visual Studio и любой стандартный редактор. Специализированный редактор также при необходимости могут создаваться с помощью фабрики редактора.

 Создать фабрику редактора, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс. Следующий пример иллюстрирует способ реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> создать фабрику редактора:

 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]

 При первом открытии типом файла, обрабатываемых редактором, загруженных в редакторе. Вы можете открыть конкретного редактора или редактора по умолчанию. Если выбрать редактор по умолчанию, определяет правильный редактор, чтобы открыть интегрированную среду разработки (IDE), который затем открывается. Дополнительные сведения см. в разделе [определить, какой редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).

## <a name="register-editor-factories"></a>Регистрация фабрик редактора
 Прежде чем использовать редактор, который вы создали, сначала необходимо зарегистрировать сведения о нем, включая расширения файлов, которые он может обрабатывать.

 Если VSPackage записывается в управляемом коде, можно использовать метод Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для регистрации фабрики редактора, после загрузки VSPackage. Если VSPackage записывается в неуправляемом коде, то необходимо зарегистрировать фабрику редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> службы.

### <a name="register-an-editor-factory-by-using-managed-code"></a>Зарегистрировать фабрику редактора с помощью управляемого кода
 Необходимо зарегистрировать фабрику редактора в вашего VSPackage `Initialize` метод. Сначала вызвать `base.Initialize`, а затем вызвать <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для каждой фабрики редактора

 В управляемом коде нет необходимости отменить регистрацию фабрику редактора, поскольку VSPackage это будет сделано автоматически. Кроме того Если фабрикой редактора реализует <xref:System.IDisposable>, объект автоматически удаляется при отмене регистрации.

### <a name="register-an-editor-factory-by-using-unmanaged-code"></a>Зарегистрировать фабрику редактора с помощью неуправляемого кода
 В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации для пакета редактора, используйте `QueryService` метод для вызова `SVsRegisterEditors`. Это возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод путем передачи реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс. Необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> в отдельном классе.

## <a name="the-editor-factory-registration-process"></a>Процесс регистрации фабрики редактора
 Следующая процедура выполняется, когда Visual Studio загружает редактора, с помощью фабрики редактора:

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Проекта системные вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

2. Этот метод возвращает фабрику редактора. Visual Studio задержки загрузки пакета редактора, тем не менее, пока система проектов необходимы редактора.

3. Редактор требованиями к системе проекта, Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, специализированный метод, который возвращает представление документа и документа объектов данных.

4. Если вызовы в Visual Studio с помощью редактора фабрики <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> возвращают объект данных документа и объект представления документа, Visual Studio создает окно документа, помещает его в объекте представления документа затем делает запись в работающей документ Таблица (RDT) для объекта данных документа.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
- [таблице выполняющихся документов](../extensibility/internals/running-document-table.md)