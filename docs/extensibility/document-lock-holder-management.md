---
title: "Управление владельца блокировки документами | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>Управление владельца блокировки документа
Выполнение документа таблицы (RDT) ведет подсчет открытые документы и любые блокировки изменить их. Можно разместить блокировки на изменение документа в RDT, если программно изменить в фоновом режиме без пользователя видеть документ в окне документа. Эта функциональность часто используется конструкторами, которые изменяют несколько файлов с помощью графического интерфейса.  
  
## <a name="document-lock-holder-scenarios"></a>Сценарии владелец блокировки документа  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Файл «» имеет зависимость от файла «b»  
 Рассмотрим ситуацию, где реализации стандартного редактора «A» и тип файла «a» и каждый файл типа «» имеет ссылку на (или зависимость от) файл типа «b». Для файлов типа «b» существует стандартный редактор «B». Когда файл откроется редактор «A» «», он получает ссылку на соответствующий файл «b». Файл «b» не отображается, но можно изменить редактор «A». Редактор «A» получает ссылку на данные файла документа «b» из <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>метода и также поддерживает блокировку изменения для файла «b».</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Редактор «A» После изменения файла «b», можно уменьшить блокировки изменения положиться файл «b» путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Этот шаг можно пропустить, если бы метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>метод с параметром `dwRDTLockType` равным <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Открыть файл «b» в другом редакторе  
 В случае, если файл «b» уже открыт редактор «B» при попытке открыть его редактор «A», существует два отдельных сценария обработки:  
  
-   Если файл «b» открыт в редакторе совместимые, должны редактора «A» зарегистрировать блокировку изменения документа с помощью файла «b» <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> После завершения изменения файла «b» редактора «A» отменить регистрацию документа изменить блокировку с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   Если недопустимым образом открыт файл «b», можно либо воспользоваться редактором ««сбой, или можно разрешить представление, связанное с редактором «A» частично открыть и отобразить соответствующее сообщение об ошибке попытки открытия файла «b». Сообщение об ошибке должно предлагать пользователю закрыть файл «b» в несовместимом редакторе, а затем снова откройте файл «» с помощью редактора «A». Также можно реализовать [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>чтобы предлагать пользователю закрыть файл «b», который был открыт в несовместимом редакторе.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> Если пользователь закрывает файл «b», открытие файла «» в редакторе «A» продолжается обычным образом.  
  
## <a name="additional-document-edit-lock-considerations"></a>Вопросы блокировки Правка дополнительных документов  
 Если редактор «A» — только с документа изменить блокировку файла «b», чем в случае редактор «B» также содержит документ редактирования блокировка файла «b», вы получаете по-разному. В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **конструктор классов** является примером визуальный конструктор, который не удерживает блокировки на изменение связан файл кода. То есть если пользователь имеет схему классов открыть в режиме конструктора и соответствующим файлом кода открыть одновременно и пользователь изменяет файл кода, но не сохраняет изменения, изменения теряются также для схемы классов (CD) файл. Если **конструктор классов** имеет только документа изменить блокировку на файл кода, у пользователя не запрашивается для сохранения изменений при закрытии файла кода. IDE пользователю предлагается сохранить изменения только после того, что пользователь закрывает **конструктор класса**. Сохраненные изменения отражаются в обоих файлах. Если оба **конструктор класса** и редактор кода файла удерживается блокировка редактирования документов на файл кода, то пользователю будет предложено сохранить при закрытии файла кода или формы. На этом этапе сохраненные изменения отражаются в форме и файлом кода. Дополнительные сведения о схемах классов см. в разделе [работа со схемами классов (конструктор классов)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Обратите внимание, что если необходимо поместить в документе не редактора блокировки на изменение, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 Много раз пользовательского интерфейса конструктора, программным образом изменяет файлы кода вносит изменения в более чем одного файла. В таких случаях <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>метод отвечает за сохранение одного или нескольких документов с помощью параметра **вы хотите сохранить изменения следующих элементов?** диалоговое окно.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>См. также  
 [Таблицы запущенных документа](../extensibility/internals/running-document-table.md)   
 [Сохранение состояния и таблицы Document запущена](../extensibility/internals/persistence-and-the-running-document-table.md)
