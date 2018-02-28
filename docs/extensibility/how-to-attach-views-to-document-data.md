---
title: "Как: присоединение представления для документирования данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>Как: присоединение представления для документирования данных
Если у вас есть новое представление документа, можно присоединить ее к существующему объекту данных документа.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Чтобы определить, если представление можно прикрепить к существующему объекту данных документа  
  
1.  Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  В реализации `IVsEditorFactory::CreateEditorInstance`, вызовите `QueryInterface` на существующий объект данных документа при вызове интегрированной среды разработки вашей `CreateEditorInstance` реализации.  
  
     Вызов `QueryInterface` можно просматривать существующие объект данных документа, который указывается в `punkDocDataExisting` параметра.  
  
     Точное интерфейсы, которые необходимо запросить, тем не менее, зависит от редактора, который открывает документ, как описано в шаге 4.  
  
3.  Если не удается найти соответствующие интерфейсы на существующий объект данных документа, возвращается код ошибки для редактора, указывающее, что объект данных документа несовместим с редактором.  
  
     В реализации IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, выводится сообщение уведомляет, что документ открыт в другом редакторе, а спросит, следует закрыть его.  
  
4.  Если закрыть этот документ, Visual Studio вызывает редактор фабрики второй раз. При вызове `DocDataExisting` параметр равен NULL. Затем реализации фабрики редактор можно открыть объект данных документа в собственный редактор.  
  
    > [!NOTE]
    >  Чтобы определить, можно ли работать с существующий объект данных документа, можно использовать закрытый сведения о реализации интерфейса путем приведения указателя для фактического [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] закрытая реализация класса. Например, все стандартные редакторы реализовать `IVsPersistFileFormat`, который наследует от <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Таким образом, можно вызвать `QueryInterface` для <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, код класса и совпадения пользовательская реализация идентификатор класса на существующий объект данных документа, а затем можно работать с объектом данных документа.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Если Visual Studio вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, он передает обратно указатель на существующий объект данных документа в `punkDocDataExisting` параметра, если он существует. Проверьте объект данных документа, возвращаемый в `punkDocDataExisting` для определения того, подходит ли объект данных документа для редактора, как описано в в примечании к шагу 4 процедуры в этом разделе. Если это подходит, то редактор фабрики должен предоставить во втором представлении данных, как описано в [поддержки нескольких представлений документа](../extensibility/supporting-multiple-document-views.md). В противном случае он должен отображать соответствующее сообщение об ошибке.  
  
## <a name="see-also"></a>См. также  
 [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Данные документа и представление документа в специализированных редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md)