---
title: "Представления одного и нескольких вкладки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] пользовательские - представления одного и нескольких вкладки"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Представления одного и нескольких вкладки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редактор может создать различные типы представлений.  Примером окне редактора кода, другой конструктор форм.  
  
 Multi\-нашитое представление представление, содержащее несколько вкладок.  Например, редактор HTML 2 в нижней части вкладки: **Разработать** и  **Источник**, каждые логическое представление.  Представление конструирования отображается принятое веб\-страницу, пока другое отображает html\-код, состоящий из веб\-страницы.  
  
## Доступ к представления физического  
 Физическая обзор объектов представления документа узла, каждый из которых представляет представление данных в буфере, как код или форма.  Соответственно, каждый объект представления документа имеет физическое представление \(distinct что\-то называемый физическая строка представления\), и обычно одно логическое представление.  
  
 В некоторых случаях, хотя физическое представление может иметь несколько логических представления.  Некоторые примеры редактор, имеющий окно разбиения с представлениями, параллельный или конструктор форм, который содержит представление GUI\/Design и представление кода программной части \-\- формы.  
  
 Чтобы разрешить редактор для доступа к все доступные представления физического, необходимо создать уникальную строку представления физической для каждого типа объектов представления документа, в фабрику редактора может создать.  Например, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] фабрика редактора может создать объекты представления документа для окна кода и окна конструктора форм.  
  
## Создание Multi\-Нашитые представления  
 Хотя объект представления документа должен быть связан с физическим представлением с помощью уникального физическую строку представления можно задать несколько вкладок в пределах физического обнаружения, чтобы включить просмотр данных различными способами.  В этом multi\-нашитой конфигурации, все вкладки связанные с той же физической строки представления, но дают каждой вкладке другое представление логически GUID.  
  
 Для создания multi\-нашитое представление редактора, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> интерфейс а затем связывает другое логического представления \(GUID<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) с каждой вкладки создании.  
  
 Редактор HTML Visual Studio пример редактора с представлением multi\-вкладки.  Он содержит **Разработать** и  **Источник** вкладки.  Чтобы разрешить это, variant является логическим представлением, связанный с каждой табуляции, `LOGICALVIEWID_TextView` для  **Разработать** вкладка и  `LOGICALVIEWID_Code` для  **Источник** вкладка.  
  
 Указав соответствующее логическое представление, VSPackage может получить доступ представление, соответствующее заданной цели, как создать форму, изменение код или код отладки.  Однако одно из окон должно быть указано пустая строка, и он должен соответствовать основной \(логическое представление`LOGVIEWID_Primary`\).  
  
 В следующей таблице перечислены доступные логические значения и их использование.  
  
|ИДЕНТИФИКАТОР GUID LOGVIEWID|Рекомендуется использование|  
|----------------------------------|---------------------------------|  
|`LOGVIEWID_Primary`|Значение по умолчанию или первичное представление фабрики редактора.<br /><br /> Все фабрики редактора должны поддерживать данное значение.  Это представление следует использовать пустую строку, так как ее физическую строку представления.  По крайней мере одно логическое представление должно быть присвоено данному значению.|  
|`LOGVIEWID_Debugging`|Отладка представление.  Обычно `LOGVIEWID_Debugging` сопоставление с таким же, как представление  `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Представление started **Просмотр кода** команды.|  
|`LOGVIEWID_Designer`|Представление started **Просмотр формы** команды.|  
|`LOGVIEWID_TextView`|Представление текстового редактора.  Это представление возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, из которого можно получить доступ  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Пользователю предлагается выбрать, просматривающие для использования.|  
|`LOGVIEWID_ProjectSpecificEditor`|Передается **Открыть с помощью** диалоговое окно<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> когда пользователь выбирает "редактор проекта \(по умолчанию\)," запись.|  
  
 Хотя логические GUID представления являются расширяемыми, можно использовать только указанные представления логического GUID в VSPackage.  
  
 При завершении работы Visual Studio сохраняет идентификатор GUID фабрики редактора и физических строк представления, связанных с окном документа так, что его можно использовать для повторного открытия окна документа, если решение будет открыто вновь.  Открытие окна, только если решение закрыто сохраняются в файле решения \(suo\).  Эти значения соответствуют `VSFPROPID_guidEditorType` и  `VSFPROPID_pszPhysicalView` значения, передаваемые в  `propid` параметр  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод.  
  
## Пример  
 Этот фрагмент показывает, как <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> объект используется для доступа к представление, реализующий  `IVsCodeWindow`.  В этом случае <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> служба используется для вызова  `LOGVIEWID_TextView`и запрос  <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>, который получает указатель на границе окна.  Указатель на объект представления документа, полученного вызовом метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> и указав значение  `VSFPROPID_DocView`.  Из объекта представления документа `QueryInterface` вызывается для  `IVsCodeWindow`.  Ожиданность в этом случае, что текстовый редактор и поэтому возвращается объект представления документа, возвращаемый в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод окна кода.  
  
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
  
## См. также  
 [Поддерживает несколько представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Практическое руководство: присоединение представления документа данных](../extensibility/how-to-attach-views-to-document-data.md)   
 [Создание пользовательские редакторы и конструкторы](../extensibility/creating-custom-editors-and-designers.md)