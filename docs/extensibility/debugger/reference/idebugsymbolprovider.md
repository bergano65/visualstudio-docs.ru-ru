---
title: IDebugSymbolProvider Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719169"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Этот интерфейс представляет собой поставщик символов, который предоставляет символы и типы, возвращая их в поле.

## <a name="syntax"></a>Синтаксис

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Поставщик символов должен реализовать этот интерфейс для предоставления информации о символе и введите его оценщику выражения.

## <a name="notes-for-callers"></a>Заметки для абонентов
Этот интерфейс получен с помощью `CoCreateInstance` функции COM (для неуправляемых поставщиков символов) или путем загрузки соответствующей управляемой сборки кода и мгновенного поставщика символов на основе информации, найденной в этой сборке. Двигатель отладки мгновляет поставщика символов работать в координации с оценщиком выражения. См. Пример для одного подхода к мгновенному воспроизведению этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugSymbolProvider`.

|Метод|Описание|
|------------|-----------------|
|`Initialize`|Не рекомендуется. Не используйте.|
|`Uninitialize`|Не рекомендуется. Не используйте.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Получает поле, содержащее адрес отладки.|
|`GetField`|Не рекомендуется. Не используйте.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Карты позиции документа в массив адресов отладки.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Карты контекста документа в массив адресов отладки.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Карты адреса отладки в контексте документа.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Получает язык, используемый для компиляции кода по адресу отладки.|
|`GetGlobalContainer`|Не рекомендуется. Не используйте.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Получает поле, представляющее полностью квалифицированное название метода.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Получает тип поля класса, представляющий полностью квалифицированное имя класса.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Создает регистратор для пространства имен, связанных с адресом отладки.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Отображает имя символа к типу символа.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Получает адрес отладки, который следует за заданным адресом отладки в методе.|

## <a name="remarks"></a>Примечания
Этот интерфейс карты документ позиции в отладки адреса и наоборот.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
Этот пример показывает, как мгновенно гостев символ, учитывая его GUID (отладка двигатель должен знать это значение).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
