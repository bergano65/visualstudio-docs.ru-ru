---
title: Редактор фабрики | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>Редактор фабрики
Фабрика редакторов создает редактор объектов и помещение их в рамки окна, известный как физическое представление. Он создает документ данных и объекты представления документа, необходимые для создания редакторов и конструкторов. Фабрика редакторов необходим для создания базового редактора Visual Studio и любого стандартного редактора. Пользовательский редактор также могут создаваться с помощью фабрики редактора.  
  
 Создайте фабрику редактора путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса. Следующий пример показывает, как реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> для создания фабрики редактора:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Редактор загружается при первом открытии тип файла, обработано, редактор. Вы можете открыть определенным редактором или редактором по умолчанию. Если выбрать редактор по умолчанию, интегрированной среды разработки (IDE) определяет правильный редактор для открытия, а затем открывает его. Дополнительные сведения см. в разделе [определение редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Регистрация фабрик редакторов  
 Прежде чем использовать редактор, который вы создали, сначала необходимо зарегистрировать сведения о нем, включая расширения имен файлов, которые он может обрабатывать.  
  
 Если пакет VSPackage, написанных на управляемом коде, можно использовать метод Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для регистрации фабрики редакторов после загрузки VSPackage. Если пакет VSPackage, написанные в неуправляемом коде, то необходимо зарегистрировать фабрику редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> службы.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Регистрация фабрики редактора с помощью управляемого кода  
 Необходимо зарегистрировать фабрику редактора в вашего VSPackage `Initialize` метод. Сначала вызвать `base.Initialize`, а затем вызвать метод <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для каждой фабрики редакторов  
  
 В управляемом коде нет необходимости для отмены регистрации фабрики редакторов, так как пакет VSPackage обрабатывающий это. Кроме того Если редактор фабрики реализует <xref:System.IDisposable>, автоматически удаляется, если он не зарегистрирован.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Регистрация фабрики редактора с помощью неуправляемого кода  
 В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализацию пакета редактора, используйте `QueryService` метод, вызываемый `SVsRegisterEditors`. Таким образом возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод путем передачи реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса. Необходимо ыполнить <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> в отдельном классе.  
  
## <a name="the-editor-factory-registration-process"></a>Процесс регистрации фабрики редактора  
 Следующая процедура выполняется при загрузке редактора, с помощью фабрики редактора Visual Studio:  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Проекта системные вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Этот метод возвращает фабрику редактора. Visual Studio задержки загрузки пакета редактора, тем не менее, пока система проектов фактически требуется редактор.  
  
3.  Редактор требованиями к системе проекта, Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, специализированный метод, который возвращает представление документа и документа объектов данных.  
  
4.  Если вызовы в Visual Studio с помощью редактора фабрики <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> возвращают объект данных документа и объект представления документа, Visual Studio создает окно документа, помещает объект представления документа в нем затем вносит изменение в выполняющийся документ Таблица (RDT) для объекта данных документа.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Запуск таблицы документов](../extensibility/internals/running-document-table.md)