---
title: Одноместные и многотактные представления Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699980"
---
# <a name="single-and-multi-tab-views"></a>Представления с одной и несколькими вкладками
Редактор может создавать различные типы представлений. Одним из примеров является окно редактора кода, другим является разработчик форм.

 Многослойное представление — это представление, имевававнее несколько вкладок. Например, редактор HTML имеет две вкладки внизу: **Дизайн** и **Источник**, каждая из логических представлений. Представление дизайна отображает отображенную веб-страницу, в то время как другой отображает HTML, который включает веб-страницу.

## <a name="accessing-physical-views"></a>Доступ к физическим представлениям
 Физические представления объектов представления документов, каждый из которых представляет представление данных в буфере, например код или форму. Соответственно, каждый объект представления документа имеет физическое представление (идентифицированное чем-то известным как строка физического представления) и, как правило, одно логическое представление.

 Однако в некоторых случаях физическое представление может иметь два или более логических представления. Некоторые примеры — это редактор с разделенным окном с бокопой представления, или разновидно-конструктор, который имеет представление GUI/design и представление кода за формой.

 Чтобы дать редактору доступ ко всем доступным физическим представлениям, необходимо создать уникальную строку физического представления для каждого типа объекта представления документа, который может создать фабрика редактора. Например, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] фабрика редакторов может создавать объекты представления документов для окна кода и окна конструктора форм.

## <a name="creating-multi-tabbed-views"></a>Создание многослойных представлений
 Хотя объект представления документа должен быть связан с физическим представлением через уникальную строку физического представления, можно разместить несколько вкладок в физическом представлении, чтобы обеспечить просмотр данных различными способами. В этой многокомнатной конфигурации все вкладки связаны с одной и той же строкой физического представления, но каждой вкладке дается разное логическое представление GUID.

 Чтобы создать многоэлементное представление для редактора, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> интерфейс,<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>а затем ассоциируете другой логический вид GUID ( ) с каждой создаваемым вкладкой.

 HTML-редактор Visual Studio является примером редактора с многотактным представлением. Он имеет **дизайн** и **источник** вкладок. Для этого с каждой вкладкой, `LOGICALVIEWID_TextView` для вкладки `LOGICALVIEWID_Code` **«Дизайн»** и для вкладки **«Источник»** связано другое логическое представление.

 Указав соответствующее логическое представление, VSPackage может получить доступ к представлению, соответствующему определенной цели, например, к разработке формы, коду редактирования или отладке кода. Тем не менее, одно из окон должно быть идентифицировано строкой`LOGVIEWID_Primary`NULL, и это должно соответствовать основному логическому мнению ().

 В следующей таблице перечислены доступные значения логического представления и их использование.

|LOGVIEWID GUID|Рекомендуемое использование|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|По умолчанию/первичный вид фабрики редакторов.<br /><br /> Все фабрики редакторов должны поддерживать это значение. Это представление должно использовать строку NULL в качестве физической строки представления. По крайней мере, необходимо установить одно логическое представление к этому значению.|
|`LOGVIEWID_Debugging`|Отладка представления. Как `LOGVIEWID_Debugging` правило, карты с `LOGVIEWID_Code`тем же представлением, что и .|
|`LOGVIEWID_Code`|Просмотр, запущенный командой **View Code.**|
|`LOGVIEWID_Designer`|Просмотр, запущенный командой **View Form.**|
|`LOGVIEWID_TextView`|Представление текстового редактора. Это представление, которое возвращается, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>из которого вы можете получить доступ.|
|`LOGVIEWID_UserChooseView`|Побуждает пользователя выбрать, какое представление использовать.|
|`LOGVIEWID_ProjectSpecificEditor`|Прошел **открытым с** диалоговой коробкой<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> когда пользователь выбирает запись "(редактор проекта по умолчанию)" .|

 Хотя логические представления GUIDs расширяются, вы можете использовать только логические guiD-интерфейсы, определенные в вашем VSPackage.

 При завершении работы Visual Studio сохраняет GUID фабрики редактора и строки физического представления, связанные с окном документа, чтобы его можно было использовать для повторного открытия окон документов при повторном открытии решения. В файле решения (.suo) сохраняются только окна, открытые при закрытии решения. Эти значения соответствуют `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` значениям, передаваемым в параметре `propid` метода. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>

## <a name="example"></a>Пример
 Этот фрагмент иллюстрирует, как <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> объект используется для доступа к `IVsCodeWindow`представлению, которое реализуется. В этом случае <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> используется служба <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> вызова `LOGVIEWID_TextView`и запроса, которая получает указатель на оконную раму. Указатель на объект представления документа получается <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> путем вызова `VSFPROPID_DocView`и указания значения . Из объекта представления `QueryInterface` документа, `IVsCodeWindow`требуется . В этом случае ожидается, что текстовый редактор возвращается, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> поэтому объект представления документа, возвращенный в метод, является окном кода.

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
- [Поддержка представления нескольких документов](../extensibility/supporting-multiple-document-views.md)
- [Практическое руководство. Вложение представлений в данные документа](../extensibility/how-to-attach-views-to-document-data.md)
- [Создание специализированных редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)
