---
title: Адаптация устаревшего кода в редактор | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184919"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Адаптация кода прежних версий для редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В редакторе Visual Studio есть множество функций, к которым можно получить доступ из существующих компонентов кода. В следующих инструкциях показано, как адаптировать компонент, не относящийся к MEF, например VSPackage, для использования функциональных возможностей редактора. В инструкциях также показано, как использовать адаптеры для получения служб редактора как в управляемом, так и в неуправляемом коде.  
  
## <a name="editor-adapters"></a>Адаптеры редактора  
 Адаптеры или оболочки редактора являются оболочками для объектов редактора, которые также предоставляют классы и интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop> API. Адаптеры можно использовать для перемещения между службами, не являющимися редакторами, например, командами оболочки Visual Studio и службами редактора. (Это то, как редактор в настоящее время размещается в Visual Studio.) Адаптеры также позволяют использовать устаревшие расширения редактора и языковой службы для правильной работы в Visual Studio.  
  
## <a name="using-editor-adapters"></a>Использование адаптеров редактора  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Предоставляет методы, переключающие между новыми интерфейсами редактора и устаревшими интерфейсами, а также методы, создающие адаптеры.  
  
 Если вы используете эту службу в части компонента MEF, вы можете импортировать службу следующим образом.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Если вы хотите использовать эту службу в компоненте, отличном от MEF, следуйте инструкциям в разделе "использование служб редактора Visual Studio в компоненте, отличном от MEF" Далее в этом разделе.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Переключение между новым API редактора и устаревшим API  
 Используйте следующие методы для переключения между объектом редактора и устаревшим интерфейсом.  
  
|Метод|Преобразование|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Преобразовывает коллекцию <xref:Microsoft.VisualStudio.Text.ITextBuffer> в объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Преобразовывает коллекцию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> в объект <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Преобразовывает коллекцию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> в объект <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Преобразовывает коллекцию <xref:Microsoft.VisualStudio.Text.Editor.ITextView> в объект <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Преобразовывает коллекцию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в объект <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Создание адаптеров  
 Используйте следующие методы для создания адаптеров для устаревших интерфейсов.  
  
|Метод|Преобразование|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для указанного объекта <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Создание адаптеров в неуправляемом коде  
 Все классы адаптеров регистрируются в качестве локальных для совместного создания, и их можно создать с помощью `VsLocalCreateInstance()` функции.  
  
 Все адаптеры создаются с использованием идентификаторов GUID, определенных в файле всшлидс. h в. Папка \Висуалстудиоинтегратион\коммон\инк\ установки пакета SDK для Visual Studio. Чтобы создать экземпляр Встекстбуфферадаптер, используйте следующий код.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Создание адаптеров в управляемом коде  
 В управляемом коде адаптеры можно создать так же, как описано для неуправляемого кода. Вы также можете использовать службу MEF, которая позволяет создавать адаптеры и взаимодействовать с ними. Такой способ получения адаптера обеспечивает более детализированный контроль, чем при совместном создании.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Создание адаптера для IVsTextView  
  
1. Добавьте ссылку на Microsoft.VisualStudio.Editor.dll. Убедитесь, что для `CopyLocal` установлено значение `false`.  
  
2. Создайте экземпляр класса <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , как показано ниже.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Вызовите метод `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Использование редактора Visual Studio непосредственно из неуправляемого кода  
 Пространство имен Microsoft. VisualStudio. Platform. Вседитор и пространство имен Microsoft. VisualStudio. Platform. Вседитор. Interop предоставляют интерфейсы, вызываемые COM, как интерфейсы Ивкс *. Например, интерфейс Microsoft. VisualStudio. Platform. Вседитор. Interop. Ивкстекстбуффер является COM-версией <xref:Microsoft.VisualStudio.Text.ITextBuffer> интерфейса. С помощью `IVxTextBuffer` можно получить доступ к моментальным снимкам буфера, изменить буфер, прослушивать события изменения текста в буфере и создавать точки отслеживания и диапазоны. Ниже показано, как получить доступ к элементу `IVxTextBuffer` из `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Получение Ивкстекстбуффер  
  
1. Определения для интерфейсов Ивкс * находятся в файле Вседитор. h в. Папка \Висуалстудиоинтегратион\коммон\инк\ установки пакета SDK для Visual Studio.  
  
2. Следующий код создает экземпляр текстового буфера с помощью `IVsUserData->GetData()` метода. В следующем коде `pData` является указателем на `IVsUserData` объект.  
  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Использование служб редактора Visual Studio в компоненте, отличном от MEF  
 Если у вас есть компонент управляемого кода, который не использует MEF и вы хотите использовать службы редактора Visual Studio, необходимо добавить ссылку на сборку, содержащую пакет VSPackage Компонентмоделхост, и получить свою службу Скомпонентмодел.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Использование компонентов редактора Visual Studio из компонента, не относящегося к MEF  
  
1. Добавьте ссылку на сборку Microsoft.VisualStudio.ComponentModelHost.dll в.. Папка \Common7\IDE\ установки Visual Studio. Убедитесь, что для `CopyLocal` установлено значение `false`.  
  
2. Добавьте закрытый `IComponentModel` член в класс, в котором вы хотите использовать службы редактора Visual Studio, следующим образом.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Создайте экземпляр модели компонента в методе инициализации компонента.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. После этого можно получить любую из служб редактора Visual Studio, вызвав `IComponentModel.GetService<T>()` метод для нужной службы.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
