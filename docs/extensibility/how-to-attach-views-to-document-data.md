---
title: Как прикрепить представления к данным документов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711092"
---
# <a name="how-to-attach-views-to-document-data"></a>Как прикрепить представления к документированию данных
Если у вас есть новое представление документа, вы можете прикрепить его к существующему объекту данных документа.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Определить, можно ли прикрепить представление к существующему объекту данных документа

1. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.

2. При реализации `IVsEditorFactory::CreateEditorInstance`вызова `QueryInterface` существующего объекта данных документа, `CreateEditorInstance` когда IDE вызывает вашу реализацию, обратитесь к существующему объекту данных документа.

    Вызов `QueryInterface` позволяет изучить существующий объект данных документа, который указан в параметре. `punkDocDataExisting`

    Однако точные интерфейсы, которые необходимо заразить, зависят от редактора, открывающего документ, изложенного в шаге 4.

3. Если вы не нашли соответствующие интерфейсы на существующем объекте данных документа, верните в редактор код ошибки, указывающий на то, что объект данных документа несовместим с редактором.

    При реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>IDE окно сообщений уведомляет вас о том, что документ открыт в другом редакторе, и спрашивает, хотите ли вы закрыть его.

4. Если вы закроете этот документ, то Visual Studio позвонит в редакцию во второй раз. На этом вызове `DocDataExisting` параметр равен NULL. Реализация фабрики редактора может открыть объект данных документа в собственном редакторе.

   > [!NOTE]
   > Чтобы определить, можно ли работать с существующим объектом данных документа, можно также использовать личные знания реализации интерфейса, отбросив указатель на фактический [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] класс частной реализации. Например, все стандартные `IVsPersistFileFormat`редакторы реализуют, что наследует от <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Таким образом, `QueryInterface` можно <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>вызвать идентификатор класса на существующем объекте данных документа, совпадая с идентификатором класса реализации, то можно работать с объектом данных документа.

## <a name="robust-programming"></a>Отказоустойчивость
 Когда Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> реализацию метода, она передает указатель на существующий объект данных документа в параметре, `punkDocDataExisting` если он существует. Изучите объект данных документа, возвращенный, `punkDocDataExisting` чтобы определить, подходит ли объект данных документа для редактора, как указано в примечании в шаге 4 процедуры в этой теме. Если это уместно, то фабрика редакторов должна предоставить второе представление для данных, изложенных в [поддержке нескольких представлений документов.](../extensibility/supporting-multiple-document-views.md) Если нет, то он должен отображать соответствующее сообщение об ошибке.

## <a name="see-also"></a>См. также
- [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)
- [Данные документов и представление документов в пользовательских редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md)
