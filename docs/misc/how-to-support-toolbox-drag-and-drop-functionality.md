---
title: "Практическое руководство. Поддержка функциональности перетаскивания в панели элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "перетаскивание, поддержка в панели элементов"
  - "панель элементов [Visual Studio SDK], клиент"
  - "панель элементов [Visual Studio SDK], перетаскивание"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# Практическое руководство. Поддержка функциональности перетаскивания в панели элементов
> [!NOTE]
>  Рекомендуется добавлять пользовательские элементы управления на панель элементов с помощью шаблонов элементов управления панели элементов, входящих в состав пакета SDK для Visual Studio 10, которые поддерживают перетаскивание. Этот раздел сохранен для обратной совместимости, а также для работы с существующими элементами управления.  
>   
>  Дополнительные сведения о создании элементов управления панели элементов с помощью шаблонов см. в разделах [Практическое руководство. Создание элемента управления панели элементов, использующего Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) и [Создание элементов управления WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Пакеты VSPackage должны реализовывать поддержку перетаскивания, если они хотят использовать элементы управления **панели элементов** в представлениях документов, таких как редакторы и конструкторы.  
  
 По умолчанию все объекты [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], производные от <xref:System.Windows.Forms.Control?displayProperty=fullName>, автоматически и прозрачно предоставляют поддержку использования элементов управления **панели элементов**, и описываемые ниже процедуры не обязательны. Базовую функциональность можно расширить путем создания конструктора.  
  
 Дополнительные сведения см. в разделах [Общие сведения о Windows Forms](../Topic/Windows%20Forms%20Overview.md) и [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
### Реализация основной функциональности перетаскивания  
  
1.  Предоставьте поддержку перетаскивания путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> в объекте представления. Это обеспечивает представление с функциональностью перетаскивания OLE и сериализацию элемента управления.  
  
     Дополнительные сведения о реализации функциональности перетаскивания см. в разделе [Перетаскивание \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole).  
  
     Вставки могут быть элементами буфера обмена или элементами управления, вставляемыми в конструктор. Сведения о стандартных форматах буфера обмена, поддерживаемых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **панелью элементов**, см. в разделе [Расширение панели элементов](../misc/extending-the-toolbox.md).  
  
2.  Предоставьте базовую реализацию интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> в представлении документов.  
  
     Когда пользователь пытается перетащить элемент управления панели элементов в представление, оболочка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] запрашивает VSPackage представления, чтобы узнать, реализует ли он интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
    1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>, чтобы возвращать <xref:Microsoft.VisualStudio.VSConstants.S_OK> для форматов **панели элементов**, которые поддерживаются местом вставки. В приведенном ниже примере проверяется, находится ли объект данных в пользовательском формате буфера обмена \(`CF_CUSTOM_FORMAT`\), и является ли объект элементом управления ActiveX.  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         IDE проверяет эти сведения при первой загрузке окна представления и для каждой активации окна представления после сброса **панели элементов** пользователем через диалоговое окно **Настройка панели элементов** IDE. Как правило, в **панели элементов** не отображаются неподдерживаемые элементы **панели элементов**.  
  
         Пользователи могут задать постоянное отображение всех страниц панели элементов. В таком случае среда не запрашивает редактор для получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>.  
  
    2.  После того как реализация <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> \(например, как описанная выше\) успешно обработает вставленный компонент, объект представления должен уведомить об этом среду [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] путем вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A>  
  
     При желании VSPackage может расширить поддержку перетаскивания, расширив свою реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
3.  Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> может поддерживать перетаскивание элементов **панели элементов** в окно путем выбора вместо действия мыши. Например, перетаскивание элемента, когда пользователь дважды щелкает элемент в **панели элементов**, или когда пользователь щелкает его один раз, а затем нажимает клавишу ВВОД. Для этого:  
  
    1.  Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A>.  
  
         Этот метод, вызываемый IDE, выбирается путем щелчка или нажатия клавиши ВВОД.  
  
         Метод должен вставлять элемент **панели элементов** в целевое окно.  
  
    2.  Если вы не хотите поддерживать реализацию путем выбора, этот метод должен возвращать <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>.  
  
         В примере ниже реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> проверяет, поддерживается ли выбранный объект, и в этом случае десериализует его в код:  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  Выполните следующие действия, чтобы убедиться, что для вашего приложения поддерживается соответствующий фокус.  
  
    1.  Если окно редактора реализует две различные области, а не два разных представления, то вызывайте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> при переключении между областями в окне редактора. Только вы знаете, когда происходит изменение активации в окне.  
  
    2.  Чтобы правильно активировать окно и обеспечить правильное обновление маршрутизации команд, вы должны вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> в компоненте. Это действие необходимо выполнить при установке фокуса в окне компонента, таком как редактор, созданный или измененной операцией перетаскивания с панели элементов.  
  
 VSPackage может потребоваться вмешательство в операцию перетаскивания и изменение вставленного элемента через интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
 Например, вместо явного добавления нового элемента управления **панели элементов** в **панель элементов** VSPackage может перехватить стандартную **панель элементов** при ее вставке и заменить ее на собственную реализацию.  
  
### Динамическое изменение элементов управления  
  
1.  Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
     Каждый раз, когда элемент **панели элементов** выбирается или вставляется, **панель элементов** запрашивает место вставки, чтобы узнать, поддерживается ли в нем интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>, и в этом случае вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A>.  
  
2.  Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> должен возвращать новый объект <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>, который следует использовать вместо исходного <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>.  
  
     Если в месте вставки не требуется переопределять объект данных, этот метод должен возвращать его входные данные.  
  
 VSPackage может разрешить пользователям циклически проходить по содержимому буфера обмена, нажимая сочетание клавиш CTRL\+SHIFT\+V.  
  
### Поддержка кольца буфера обмена  
  
1.  Реализуйте обработчик для команды `CMDIDPasteNextTBXCBItem` с помощью:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> для пакетов VSPackage на основе сборки взаимодействия;  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> для пакетов VSPackage на основе Managed Package Framework; интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler>.  
  
2.  В обработчике команды реализуйте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A>, чтобы определить, существуют ли какие\-либо объекты буфера обмена для циклического перебора.  
  
    1.  Если элементы в буфере обмена панели элементов отсутствуют, среда проверяет системный буфер обмена, чтобы узнать, есть ли в нем какие\-либо элементы.  
  
    2.  Если элементы присутствуют в системном буфере обмена, но не в буфере обмена панели элементов, то кольцо буфера обмена заполняется системными элементами.  
  
    3.  Для выбора следующего элемента в списке реализация вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A>.  
  
    4.  Чтобы вернуться к началу цикла буфера обмена, вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A>.  
  
## См. также  
 [Расширение панели элементов](../misc/extending-the-toolbox.md)   
 [Практическое руководство. Предоставление настраиваемых элементов панели элементов с помощью сборок взаимодействия](../Topic/How%20to:%20Provide%20Custom%20Toolbox%20Items%20By%20Using%20Interop%20Assemblies.md)   
 [Разработка расширенных элементов управления панели элементов](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Регистрация возможностей поддержки панели элементов](../misc/registering-toolbox-support-features.md)   
 [Управление панелью элементов](/visual-cpp/misc/managing-the-toolbox)