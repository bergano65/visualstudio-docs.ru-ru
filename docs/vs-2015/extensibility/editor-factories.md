---
title: Фабрики редакторов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97f53e944e140948b769c351fef6c9b91f4aa008
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246913"
---
# <a name="editor-factories"></a>Фабрики редакторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фабрику редактора создает объекты редактор и помещает их в рамку окна, известный как физическое представление. Он создает данные документа и объекты представления документа, которые необходимы для создания в редакторах и конструкторах. Фабрику редактора необходима для создания базового редактора Visual Studio и любой стандартный редактор. Специализированный редактор также при необходимости могут создаваться с помощью фабрики редактора.  
  
 Создать фабрику редактора, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс. Следующий пример иллюстрирует способ реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> создать фабрику редактора:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 При первом открытии типом файла, обрабатываемых редактором, загруженных в редакторе. Вы можете открыть конкретного редактора или редактора по умолчанию. Если выбрать редактор по умолчанию, определяет правильный редактор, чтобы открыть интегрированную среду разработки (IDE), который затем открывается. Дополнительные сведения см. в разделе [определить, какой редактор открывает файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Регистрация фабрик редактора  
 Прежде чем использовать редактор, который вы создали, сначала необходимо зарегистрировать сведения о нем, включая расширения файлов, которые он может обрабатывать.  
  
 Если VSPackage записывается в управляемом коде, можно использовать метод Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для регистрации фабрики редактора, после загрузки VSPackage. Если VSPackage записывается в неуправляемом коде, то необходимо зарегистрировать фабрику редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> службы.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Регистрация фабрику редактора с помощью управляемого кода  
 Необходимо зарегистрировать фабрику редактора в вашего VSPackage `Initialize` метод. Сначала вызвать `base.Initialize`, а затем вызвать <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для каждой фабрики редактора  
  
 В управляемом коде нет необходимости отменить регистрацию фабрику редактора, поскольку VSPackage это будет сделано автоматически. Кроме того Если фабрикой редактора реализует <xref:System.IDisposable>, объект автоматически удаляется при отмене регистрации.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Регистрация фабрику редактора с помощью неуправляемого кода  
 В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации для пакета редактора, используйте `QueryService` метод для вызова `SVsRegisterEditors`. Это возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод путем передачи реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс. Необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> в отдельном классе.  
  
## <a name="the-editor-factory-registration-process"></a>Процесс регистрации фабрики редактора  
 Следующая процедура выполняется, когда Visual Studio загружает редактора, с помощью фабрики редактора:  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Проекта системные вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2.  Этот метод возвращает фабрику редактора. Visual Studio задержки загрузки пакета редактора, тем не менее, пока система проектов необходимы редактора.  
  
3.  Редактор требованиями к системе проекта, Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, специализированный метод, который возвращает представление документа и документа объектов данных.  
  
4.  Если вызовы в Visual Studio с помощью редактора фабрики <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> возвращают объект данных документа и объект представления документа, Visual Studio создает окно документа, помещает его в объекте представления документа затем делает запись в работающей документ Таблица (RDT) для объекта данных документа.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Запуск таблицы документов](../extensibility/internals/running-document-table.md)

