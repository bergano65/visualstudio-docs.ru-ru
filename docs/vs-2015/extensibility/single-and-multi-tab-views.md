---
title: Представления одной и несколькими вкладками | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 804a37a43ffe25335dc522542f5035b0882e63ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205562"
---
# <a name="single-and-multi-tab-views"></a>Представления с одной и несколькими вкладками
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор можно создавать различные типы представлений. Одним из примеров является окном редактора кода, другой — это конструктор форм.  
  
 Представление с несколькими вкладками — представление, которое содержится несколько вкладок. Например в редакторе HTML есть две вкладки в нижней: **Проектирование** и **источника**, каждая логическое представление. В конструкторе отображаются готовой веб-страницы, а другой код HTML, который состоит из веб-страницы.  
  
## <a name="accessing-physical-views"></a>Доступ к физической представлениям  
 Физические представления разместить объекты представления документа, каждый из которых представляет представление данных в буфере, например код или формы. Соответственно каждый объект представления документа имеет физического представления, (определяется по что-нибудь, известный как строка физического представления) и обычно одно логическое представление.  
  
 Однако в некоторых случаях физическое представление может иметь два или несколько логических представлений. Примерами являются редактор, который имеет разделенного окна с представлениями side-by-side, или конструктор форм, имеющий представление графического пользовательского интерфейса и кода и кода behind--представление формы.  
  
 Чтобы включить редактора, чтобы получить доступ ко всем доступных физических представлений, необходимо создать строка физического представления, уникальный для каждого типа объекта представления документа, который может создать фабрику редактора. Например [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] фабрика редакторов может создать документ Просмотр объектов для окна кода и окна конструктора форм.  
  
## <a name="creating-multi-tabbed-views"></a>Создание представлений с несколькими вкладками  
 Хотя объект представления документа должна быть связана с физическое представление по строке уникальный физического представления, можно поместить несколько вкладок на физическое представление для просмотра данных по-разному. В этой конфигурации с несколькими вкладками все вкладки связаны с этой же строкой физического представления, но каждая вкладка присваивается разных идентификаторов GUID логических представлений.  
  
 Чтобы создать представление с несколькими вкладками для редактора, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> интерфейс, а затем привязывать их различных идентификаторов GUID логических представлений (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) с каждой вкладки можно создать.  
  
 Редактор Visual Studio HTML приведен пример с несколькими вкладками представление редактора. Он имеет **разработки** и **источника** вкладки. Для этого другое представление логический связан с каждой из вкладок `LOGICALVIEWID_TextView` для **разработки** вкладку и `LOGICALVIEWID_Code` для **источника** вкладки.  
  
 Указав соответствующее логическое представление, VSPackage может получить доступ к представлению, которое соответствует определенной цели, например разработке формы, редактирование кода или отладке кода. Тем не менее, одно из окон должен быть идентифицирован строку NULL, и он должен соответствовать основной логическое представление (`LOGVIEWID_Primary`).  
  
 Ниже перечислены доступные логическое представление значений и их использовании.  
  
|ИДЕНТИФИКАТОР GUID LOGVIEWID|Рекомендации по использованию|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Представление по умолчанию источник фабрики редактора.<br /><br /> Всех фабрик редакторов должен поддерживать это значение. В этом представлении необходимо использовать строку NULL в качестве его строка физического представления. Это значение должно быть присвоено хотя бы одно логическое представление.|  
|`LOGVIEWID_Debugging`|Представление отладки. Как правило `LOGVIEWID_Debugging` сопоставляется же представление, что `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Представление, запускаемого по **Просмотр кода** команды.|  
|`LOGVIEWID_Designer`|Представление, запускаемого по **форма просмотра** команды.|  
|`LOGVIEWID_TextView`|Представление текстового редактора. Это представление, которое возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, из которого вы можете получить доступ к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Предлагает пользователю выбрать представление, которое требуется использовать.|  
|`LOGVIEWID_ProjectSpecificEditor`|Передаваемый по **открыть с помощью** диалоговое окно<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Когда пользователь выбирает элемент "(редактор проектов по умолчанию)».|  
  
 Несмотря на то, что идентификаторов GUID логических представлений расширяемы, можно использовать только идентификаторы GUID логического представления, определенные в пакете VSPackage.  
  
 При завершении работы Visual Studio сохраняет идентификатор GUID фабрики редактора, а также физическое представление строки, связанный с окном документа, чтобы его можно использовать повторно открыть окна документов, когда решение открывается повторно. Только windows, которые открыты при закрытии решения, сохраняются в файле решения (SUO). Эти значения соответствуют `VSFPROPID_guidEditorType` и `VSFPROPID_pszPhysicalView` значениями, передаваемыми в `propid` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
## <a name="example"></a>Пример  
 В этом фрагменте показано, как <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> объект используется для доступа к представлению, который реализует `IVsCodeWindow`. В этом случае <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> службы используется для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> и запрос `LOGVIEWID_TextView`, которая получает указатель на рамку окна. Указатель на объект представления документа получается путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> и указав значение `VSFPROPID_DocView`. Из объекта представления документа `QueryInterface` вызывается для `IVsCodeWindow`. В этом случае ожидается, что возвращается в текстовом редакторе, и поэтому объекта представления документа возвращены в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метода является окном кода.  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Поддержка представления нескольких документов](../extensibility/supporting-multiple-document-views.md)   
 [Практическое руководство. Присоединение представлений в данные документа](../extensibility/how-to-attach-views-to-document-data.md)   
 [Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)
