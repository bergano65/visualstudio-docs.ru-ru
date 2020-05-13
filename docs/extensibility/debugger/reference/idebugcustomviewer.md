---
title: IDebugCustomViewer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732417"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Этот интерфейс позволяет оценщику выражения (EE) отображать ценность свойства в любом формате, который необходим.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
EE реализует этот интерфейс для отображения стоимости свойства в пользовательском формате.

## <a name="notes-for-callers"></a>Заметки для абонентов
Вызов функции `CoCreateInstance` COM мгновенно передает этот интерфейс. Передаваемый `CLSID` `CoCreateInstance` в получается из реестра. Звонок [в GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) получает место в реестре. Смотрите комментарии для получения подробной информации, а также пример.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Делает все необходимое для отображения заданного значения.|

## <a name="remarks"></a>Примечания
Этот интерфейс используется, когда значение свойства не может отображаться обычными средствами, например, с таблицей данных или другим сложным типом свойств. Пользовательский зритель, представленный `IDebugCustomViewer` интерфейсом, отличается от визуализатора типа, который является внешней программой для отображения данных определенного типа независимо от EE. EE реализует пользовательский зритель, который специфичен для этого EE. Пользователь выбирает, какой тип визуализатора использовать, будь то визуализатор типа или пользовательский зритель. Подробную информацию об этом процессе можно узнать из [данных визуализации и просмотра.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

Пользовательский зритель регистрируется так же, как EE и, следовательно, требует языка GUID и поставщика GUID. Точная метрика (или имя регистрации) известна только EE. Эта метрика возвращается в структуру [DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) которая, в свою очередь, возвращается по вызову [в GetCustomViewerList.](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Значение, хранящееся в метрике, передается `CLSID` функции `CoCreateInstance` COM (см. пример).

Функция [SDK Helpers для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`может быть использована для регистрации пользовательского просмотра. Ознакомьтесь с разделом реестра `Debugging SDK Helpers` "Оценщики экспрессии" для конкретных ключей реестра, в которых нуждается пользовательский зритель. Обратите внимание, что пользовательскому зрителю нужна только одна метрика (которая определяется исполнителем EE), в то время как оценщику выражения требуется несколько предопределенных метрик.

Обычно пользовательский зритель предоставляет только для чтения представление данных, так как интерфейс [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) поставляемый [в DisplayValue,](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) не имеет методов для изменения значения свойства, за исключением строки. Для поддержки изменяющихся произвольных блоков данных EE реализует пользовательский `IDebugProperty3` интерфейс на том же объекте, который реализует интерфейс. Этот пользовательский интерфейс будет предоставлять методы, необходимые для изменения произвольного блока данных.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
Этот пример показывает, как получить первый пользовательский зритель из свойства, если это свойство имеет какой-либо пользовательских зрителей.

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
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
