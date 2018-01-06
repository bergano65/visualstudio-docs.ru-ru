---
title: "IDebugCustomViewer | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer
helpviewer_keywords: IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9bbe546ffb3c6e61b251e8afbfc7fa9018ffa1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Этот интерфейс позволяет вычислитель выражений (Эстония) для отображения значения свойства в формате необходим.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 EE реализует этот интерфейс для отображения значения свойства в пользовательском формате.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов COM `CoCreateInstance` функция создает экземпляр этого интерфейса. `CLSID` Передаваемый `CoCreateInstance` берется из реестра. Вызов [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Получает расположение в реестре. Сведения, а также пример см. заметки.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Выполняет все необходимые для отображения заданного значения.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется в том случае, когда не удается отобразить значение свойства обычным способом — например, с помощью таблицы данных или другой тип сложного свойства. Пользовательское средство просмотра, представленный как `IDebugCustomViewer` интерфейсом, отличается от визуализатор тип, который является внешней программой для отображения данных определенного типа независимо от EE. EE реализует пользовательское средство просмотра, относящиеся к этой EE. Пользователь выбирает, какой тип визуализатора для использования, будь то тип визуализатора или пользовательское средство просмотра. В разделе [Visualizing и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) подробные сведения об этом процессе.  
  
 Пользовательское средство просмотра регистрируется в так же, как EE и, следовательно, требует GUID языка и GUID поставщика. Точные метрики (или имя записи реестра) известен только EE. Эта метрика возвращается в [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структуру, которая в свою очередь, возвращается путем вызова [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Значение, хранящееся в метрику — `CLSID` передается COM `CoCreateInstance` функцию (см. пример).  
  
 [SDK вспомогательные методы для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функции `SetEEMetric`, можно использовать для регистрации пользовательское средство просмотра. Обратитесь к разделу реестра «Вычислители выражений» `Debugging SDK Helpers` для ключей реестра, который требуется пользовательское средство просмотра. Обратите внимание, что пользовательское средство просмотра требуется только один показатель (который определяется исполнитель EE) а вычислитель выражений требует нескольких предопределенные метрики.  
  
 Как правило, пользовательское средство просмотра предоставляет только для чтения представление данных, поскольку [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) предоставленный интерфейс [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) не имеет методов, для изменения значения свойства, за исключением того, как строка. Чтобы поддерживать изменение произвольный блоков данных, EE реализует пользовательский интерфейс на тот же объект, реализующий `IDebugProperty3` интерфейса. Этот пользовательский интерфейс будет затем предоставить методы, необходимые для изменения произвольный блока данных.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить первый пользовательское средство просмотра из свойства, если это свойство имеет любые пользовательские средства просмотра.  
  
```cpp  
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
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Вспомогательные функции пакета SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)