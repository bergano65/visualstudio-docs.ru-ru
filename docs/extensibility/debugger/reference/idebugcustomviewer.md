---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "Интерфейс IDebugCustomViewer"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет средство оценки выражений \(EE\) для отображения значения свойства в любой формат является обязательным.  
  
## Синтаксис  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## Примечания по реализации  
 EE реализует этот интерфейс для отображения значения свойства в пользовательском формате.  
  
## Замечания для вызывающих объектов  
 Вызов модели COM `CoCreateInstance` создает функции этот интерфейс.  `CLSID` передается методу  `CoCreateInstance` возвращает из реестра.  Вызов [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) получает расположение в реестре.  Дополнительные сведения см. в разделе " примечания ", а также примера.  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Выполняет все действия, необходимые для отображения заданного значения.|  
  
## Заметки  
 Этот интерфейс используется, если значение свойства не может быть отображается обычным середин\-для примера с таблицей данных или другим сложным типом свойства.  Пользовательское средство, как представлено `IDebugCustomViewer` интерфейс визуализатора, отличается от типа, внешняя программа для вывода данных конкретного типа, независимо от EE.  EE реализует пользовательское средство просмотра, относящихся к этому EE.  Пользователь выбирает тип визуализатора, оно визуализатор типов или настраиваемого средства просмотра.  См. [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) дополнительные сведения об этом процессе.  
  
 Пользовательский средство просмотра зарегистрирован точно так же, как и EE и, следовательно, требует идентификатор GUID языка и GUID поставщика.  Явная показатель \(или имя записи реестра\) известны только к EE.  Данная метрика возвращается в [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структура которой, в свою очередь, возвращает вызовом  [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md).  Значение, хранящееся в метрике `CLSID` то передается в модели COM  `CoCreateInstance` функция \(см. пример\).  
  
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функция  `SetEEMetric`может использоваться для регистрации пользовательского средства просмотра.  См. раздел реестра "средства оценки выражений" `Debugging SDK Helpers` для отдельных разделов реестра, пользовательское средство просмотра требуется.  Обратите внимание, что пользовательское средство просмотра нужна только одна показатель \(которая определена разработчик EE\), в то время как средство оценки выражений требуется несколько стандартных показателей.  
  
 Обычно пользовательское средство просмотра предоставляет только для чтения представление данных с [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, предоставляемый в  [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) не содержит методы для изменения значения этого свойства, за исключением строк.  Для поддержки изменить произвольные блоков данных, EE реализует пользовательский интерфейс для одного и того же объекта, реализующего `IDebugProperty3` интерфейс.  Этот пользовательский интерфейс затем предоставил бы методы, необходимые для изменения произвольный блок данных.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Пример  
 В этом примере показано, как получить первого пользовательского средства просмотра из свойства, если свойство имеет любых пользовательских средств просмотра.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)