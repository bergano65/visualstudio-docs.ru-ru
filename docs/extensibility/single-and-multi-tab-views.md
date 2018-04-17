---
title: Представления одного и нескольких вкладка | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23feeaee14e6a149ad385c9f5e4a0c4b41be1e86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="single-and-multi-tab-views"></a>Одной или несколькими вкладку представления
Редактор можно создавать различные типы представлений. Примером служит окно редактора кода, другая — конструктор форм.  
  
 Представление несколькими вкладками — представления, имеющего несколько вкладок. Например, HTML-редактор имеет две вкладки в нижней: **разработки** и **источника**, каждая логическое представление. В режиме конструктора отображаются готовый для просмотра веб-страницы, а другой код HTML, который состоит из веб-страницы.  
  
## <a name="accessing-physical-views"></a>Доступ к физической представления  
 Физические представления размещать объекты представление документа, каждый из которых представляет данные в буфере, например код или формы в представлении. Таким образом каждый объект представления документа имеет физическое представление (определяется как строка физическое представление сведений) и обычно одно логическое представление.  
  
 Хотя в некоторых случаях физическое представление может иметь два или более логических представлений. Примеры — с разделением окна с представлениями side-by-side редактор или конструктор форм с графическим интерфейсом пользователя или конструктор и код фонового-представление формы.  
  
 Чтобы включить редактора для доступа ко всем доступных физических представлений, необходимо создать уникальный физическое представление строка для каждого типа объекта представления документа, можно создать фабрику редактора. Например [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] фабрики редактора можно создать документ Просмотр объектов для окна кода и окно конструктора форм.  
  
## <a name="creating-multi-tabbed-views"></a>Создание представлений с несколькими вкладками  
 На то, что объект представления документа должен быть сопоставлен физическое представление в строке уникальный физическое представление, можно разместить несколько вкладок в физическое представление для просмотра данных по-разному. В этой конфигурации с несколькими вкладками все вкладки связаны с одной и той же строке физическое представление, но каждая вкладка имеет другой логическое представление идентификатора GUID.  
  
 Чтобы создать представление несколькими вкладками для редактора, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> интерфейс, а затем сопоставить различные логическое представление идентификатора GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) с помощью вкладок вы создаете.  
  
 Редактор Visual Studio HTML является примером редактор с несколькими вкладку представления. Он имеет **разработки** и **источника** вкладок. Чтобы включить эту возможность, другой логическое представление связан с каждой из вкладок `LOGICALVIEWID_TextView` для **разработки** вкладку и `LOGICALVIEWID_Code` для **источника** вкладки.  
  
 Указав соответствующее логическое представление, VSPackage можно получить доступ к представлению, которое соответствует для определенной цели, например разработке формы редактирования кода и отладка кода. Тем не менее, одно из окон, должен быть идентифицирован по ПУСТУЮ строку, и это должно соответствовать основной логическое представление (`LOGVIEWID_Primary`).  
  
 В следующей таблице перечислены доступные логическое представление значений и их использовании.  
  
|ИДЕНТИФИКАТОР GUID LOGVIEWID|Рекомендации по использованию|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Представление по умолчанию источник фабрики редактора.<br /><br /> Всех фабрик редакторов должен поддерживать это значение. В этом представлении должны использовать ПУСТУЮ строку в качестве его физическое представление строки. Это значение должно быть присвоено хотя бы одно логическое представление.|  
|`LOGVIEWID_Debugging`|Представление отладки. Как правило `LOGVIEWID_Debugging` сопоставляется с тем же самым представлением как `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Представление, запускаемого по **Просмотр кода** команды.|  
|`LOGVIEWID_Designer`|Представление, запускаемого по **Просмотр формы** команды.|  
|`LOGVIEWID_TextView`|Представление текстового редактора. Это представление, которое возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, из которого можно открыть <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Предлагает пользователю выбрать представление, которое требуется использовать.|  
|`LOGVIEWID_ProjectSpecificEditor`|Передаваемый по **открыть с помощью** диалоговое окно<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Когда пользователь выбирает запись «(проект по умолчанию редактор)».|  
  
 Несмотря на то, что логическое представление идентификатора GUID являются расширяемыми, можно использовать только логическое представление GUID, определенный в пакете VSPackage.  
  
 При завершении работы Visual Studio сохраняет GUID фабрики редакторов и физическое представление строки, связанные с окном документа, чтобы его можно повторно открыть окна документов, когда решение открывается повторно. Только для windows, которые открыты при закрытии решения, сохраняются в файле решения (SUO). Эти значения соответствуют `VSFPROPID_guidEditorType` и `VSFPROPID_pszPhysicalView` значения, передаваемые в `propid` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
## <a name="example"></a>Пример  
 В этом фрагменте показано, как <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> объект используется для доступа к представлению, который реализует `IVsCodeWindow`. В этом случае <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> службы используется для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> и запрос `LOGVIEWID_TextView`, которая получает указатель на фрейм окна. Указатель на объект представления документа, полученного путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> и указав значение `VSFPROPID_DocView`. Из объект представления документа `QueryInterface` вызывается для `IVsCodeWindow`. В этом случае предполагается, что возвращается в текстовом редакторе, и поэтому возвращается объект представления документа в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод — это окно кода.  
  
```cpp  
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
 [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Как: присоединение представления для документирования данных](../extensibility/how-to-attach-views-to-document-data.md)   
 [Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)