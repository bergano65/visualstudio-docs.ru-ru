---
title: Фабрики редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197764"
---
# <a name="editor-factories"></a>Фабрики редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фабрика редактора создает объекты редактора и помещает их в рамку окна, называемую физическим представлением. Он создает данные документа и объекты представления документов, необходимые для создания редакторов и конструкторов. Фабрика редактора необходима для создания основного редактора Visual Studio и любого стандартного редактора. Настраиваемый редактор можно также создать с помощью фабрики редактора.  
  
 Фабрика редактора создается путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса. В следующем примере показано, как реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> для создания фабрики редактора:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Редактор загружается при первом открытии типа файла, обрабатываемого этим редактором. Можно открыть либо конкретный редактор, либо редактор по умолчанию. При выборе редактора по умолчанию интегрированная среда разработки (IDE) определяет нужный редактор для открытия, а затем открывает его. Дополнительные сведения см. [в разделе Определение редактора, открывающего файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Регистрация фабрик редактора  
 Прежде чем можно будет использовать созданный редактор, сначала необходимо зарегистрировать сведения о нем, включая расширения файлов, которые он может обменяться.  
  
 Если пакет VSPackage написан на управляемом коде, можно использовать метод Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для регистрации фабрики редактора после загрузки VSPackage. Если пакет VSPackage написан в неуправляемом коде, необходимо зарегистрировать фабрику редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> службы.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Регистрация фабрики редактора с помощью управляемого кода  
 Фабрику редактора необходимо зарегистрировать в `Initialize` методе VSPackage. Первый вызов `base.Initialize` , а затем вызов <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для каждой фабрики редактора  
  
 В управляемом коде нет необходимости отменять регистрацию фабрики редактора, так как пакет VSPackage будет выполнять эту обработку. Кроме того, если фабрика редактора реализует <xref:System.IDisposable> , она автоматически удаляется при отмене регистрации.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Регистрация фабрики редактора с помощью неуправляемого кода  
 В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации для пакета редактора используйте `QueryService` метод для вызова `SVsRegisterEditors` . При этом возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод, передав реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейса. Необходимо еализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> в отдельный класс.  
  
## <a name="the-editor-factory-registration-process"></a>Процесс регистрации фабрики редакторов  
 Следующая процедура выполняется, когда Visual Studio загружает редактор с помощью фабрики редактора:  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Система проектов вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Этот метод возвращает фабрику редактора. Тем не менее Visual Studio задерживает загрузку пакета редактора, пока системе проектов действительно не понадобится редактор.  
  
3. Когда системе проектов требуется редактор, Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Специальный метод, который возвращает как представление документа, так и объекты данных документа.  
  
4. Если вызовы Visual Studio к фабрике редактора с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> возвращают как объект данных документа, так и объект представления документа, Visual Studio создает окно документа, помещает в него объект представления документа и выполняет запись в таблицу выполняемого документа (РДТ) для объекта данных документа.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Запуск таблицы документов](../extensibility/internals/running-document-table.md)
