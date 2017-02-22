---
title: "Адаптация кода прежних версий для редактора | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - адаптеры"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Адаптация кода прежних версий для редактора
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В редакторе Visual Studio имеет множество функций, которые можно получить из существующих компонентов кода. Ниже показано, как адаптировать компонент не MEF, например, VSPackage, чтобы использовать функциональные возможности редактора. Инструкции также показано, как использовать адаптеры для получения служб редактора в управляемом и неуправляемом коде.  
  
## Редактор адаптеров  
 Редактор адаптеров или оболочки, являются оболочками для редактора объектов, которые также предоставляют классы и интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop> API. Можно использовать адаптеры для перемещения между службы не редактора, например, команд оболочки Visual Studio и редактор служб. \(Это как редактор в настоящее время размещены в Visual Studio.\) Адаптеры позволяют также прежних версий редактора и язык расширения служб для правильной работы в Visual Studio.  
  
## С помощью редактора адаптеров  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Предоставляет методы, которые переключаются между новых интерфейсов редактора и устаревшие интерфейсы и методы, создающие адаптеров.  
  
 При использовании этой службы в части компонентов MEF, можно импортировать службы следующим образом.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Если вы хотите использовать эту службу в компонент не MEF, следуйте инструкциям в разделе «Использование Visual Studio редактора в MEF не компонент служб» далее в этом разделе.  
  
## Переключение между прежних версий и новый API редактора  
 Для переключения между традиционным интерфейсом и редактор объекта, используйте следующие методы.  
  
|Метод|преобразование|  
|-----------|--------------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Преобразует <xref:Microsoft.VisualStudio.Text.ITextBuffer> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Преобразует <xref:Microsoft.VisualStudio.Text.Editor.ITextView> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Преобразует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## Создание адаптеров  
 Используйте следующие методы для создания адаптеров для устаревшие интерфейсы.  
  
|Метод|преобразование|  
|-----------|--------------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Создает объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для указанного <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Создает объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## Создание адаптеров в неуправляемом коде  
 Все классы адаптеров регистрируются в качестве локальных совместно создаваемый объект и может быть создан с помощью `VsLocalCreateInstance()` функции.  
  
 Все адаптеры создаются с помощью идентификатора GUID, которые определены в файле vsshlids.h в... \\VisualStudioIntegration\\Common\\Inc\\ папка установки Visual Studio SDK. Чтобы создать экземпляр VsTextBufferAdapter, используйте следующий код.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## Создание адаптеров в управляемом коде  
 В управляемом коде совместно можно создать адаптеры таким же образом, как описано для неуправляемого кода. Также можно использовать службу MEF, позволяет создавать и взаимодействовать с адаптерами. Таким способом получения адаптер обеспечивает более точное управление меньше, чем при его создании совместно.  
  
#### Создание адаптера для IVsTextView  
  
1.  Добавьте ссылку на Microsoft.VisualStudio.Editor.dll. Убедитесь, что `CopyLocal` имеет значение `false`.  
  
2.  Создать экземпляр <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, как показано ниже.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Вызовите метод `CreateX()`.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## В редакторе Visual Studio непосредственно из неуправляемого кода  
 Microsoft.VisualStudio.Platform.VSEditor пространство имен и имен Microsoft.VisualStudio.Platform.VSEditor.Interop предоставлять интерфейсы COM\-вызовов в качестве интерфейсов IVx \*. Например, интерфейс Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer — это версия COM <xref:Microsoft.VisualStudio.Text.ITextBuffer> интерфейса. Из `IVxTextBuffer`, можно получить доступ к моментальным снимкам буфера, меняющим содержимое буфера, прослушивать события изменения текста в буфере и создание точек отслеживания и диапазонов. Ниже показано, как получить доступ к `IVxTextBuffer` из `IVsTextBuffer`.  
  
#### Для получения IVxTextBuffer  
  
1.  Определения интерфейсов IVx \* находятся в файле VSEditor.h в... \\VisualStudioIntegration\\Common\\Inc\\ папка установки Visual Studio SDK.  
  
2.  Следующий код создает текстового буфера с помощью `IVsUserData->GetData()` метод. В следующем коде `pData` — это указатель на `IVsUserData` объект.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## С помощью редактора Visual Studio служб в компонент не MEF  
 При наличии существующего компонента управляемого кода, не использующих MEF и вы хотите использовать службы редактор Visual Studio, необходимо добавить ссылку на сборку, содержащую ComponentModelHost VSPackage и получить его модели SComponentModel службу.  
  
#### Чтобы использовать компоненты редактора Visual Studio из компонента не MEF  
  
1.  Добавьте ссылку на сборку Microsoft.VisualStudio.ComponentModelHost.dll в... \\Common7\\IDE\\ папка установки Visual Studio. Убедитесь, что `CopyLocal` имеет значение `false`.  
  
2.  Добавьте закрытый `IComponentModel` члена класса, в котором вы хотите использовать службы редактора Visual Studio, как показано ниже.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Создайте экземпляр модели компонентов в методе инициализации компонента.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  После этого одна из служб редактора Visual Studio можно получить, вызвав `IComponentModel.GetService<T>()` метод для службы.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```