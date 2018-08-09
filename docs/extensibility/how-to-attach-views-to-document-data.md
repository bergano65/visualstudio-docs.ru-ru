---
title: 'Практическое: вложение представлений в данные документа | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48aa6f7bc0c8ea948c43dcdff11d7ccae1cedc93
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637907"
---
# <a name="how-to-attach-views-to-document-data"></a>Практическое: вложение представлений данных документа
Если у вас есть новое представление документа, можно присоединить ее к существующему объекту данных документа.  
  
## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Чтобы определить представления можно присоединить к существующему объекту данных документа  
  
1.  Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  В реализации `IVsEditorFactory::CreateEditorInstance`, вызовите `QueryInterface` на существующий объект данных документа при вызове интегрированной среды разработки вашей `CreateEditorInstance` реализации.  
  
     Вызов `QueryInterface` можно проверять существующий объект данных документа, который указан в параметре `punkDocDataExisting` параметра.  
  
     Точное интерфейсы, которые необходимо запросить, тем не менее, зависит от редактора, который открывает документ, как описано на шаге 4.  
  
3.  Если соответствующие интерфейсы на существующий объект данных документа не найден, возвращается код ошибки для редактора, указывающее на то, что объект данных документа несовместим с помощью редактора.  
  
     В реализации IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, появится сообщение уведомляет, что документ открыт в другом редакторе и запрашивает, следует ли закрыть его.  
  
4.  Если закрыть этот документ, Visual Studio вызывает фабрикой редактора во второй раз. На этот вызов `DocDataExisting` параметр равен NULL. Реализации фабрики редактора можно затем откройте объект данных документа в ваш собственный редактор.  
  
    > [!NOTE]
    >  Чтобы определить, можно ли работать с существующим объектом данных документа, можно использовать закрытого набора знаний в реализации интерфейса путем приведения указатель на фактический [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] закрытая реализация класса. Например, реализовать все стандартные редакторы `IVsPersistFileFormat`, который наследует от <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Таким образом, можно вызвать `QueryInterface` для <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, и если идентификатор класса на существующий объект данных документа соответствует вашей реализации код класса, а затем можно работать с объектом данных документа.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Когда Visual Studio вызывает вашу реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод, он передает обратно указатель на существующий объект данных документа в `punkDocDataExisting` параметра, если он существует. Проверьте объект данных документа, возвращаемый в `punkDocDataExisting` для определения, подходит ли объект данных документа для редактора, как описано в примечании на шаге 4 процедуры в этом разделе. Если это требуется, то фабрикой редактора должен предоставить во втором представлении данных, как описано в [поддерживать несколько представлений документа](../extensibility/supporting-multiple-document-views.md). В противном случае оно должно отображать соответствующее сообщение об ошибке.  
  
## <a name="see-also"></a>См. также  
 [Поддерживает несколько представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Данные документа и представление документа в специализированных редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md)