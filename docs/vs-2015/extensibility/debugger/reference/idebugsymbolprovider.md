---
title: IDebugSymbolProvider | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b760b106992b200576258ab6becb1ae3849b8f3a
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62420931"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет поставщик символов, который предоставляет типы, возвращая их в виде полей и символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик символов необходимо реализовать этот интерфейс, чтобы указать символ и сведения о типе для вычислителя выражений.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс получается с помощью COM `CoCreateInstance` функции (поставщики неуправляемых символ) или путем загрузки соответствующего управляемого кода сборки и создания экземпляров поставщика символов на основе информации, содержащейся в этой сборке. Отладчик создает поставщик символов для работы совместно с средство оценки выражений. См. в примере один из способов создания экземпляра этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugSymbolProvider`.  
  
|Метод|Описание|  
|------------|-----------------|  
|`Initialize`|Не рекомендуется. Не используется.|  
|`Uninitialize`|Не рекомендуется. Не используется.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Получает поле, содержащее адрес отладки.|  
|`GetField`|Не рекомендуется. Не используется.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Сопоставляет позицию документов в массив адресов отладки.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Сопоставляет контекст документа в массив адресов отладки.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Сопоставляет адрес отладки к контексту документа.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Получает язык, используемый для компиляции кода по адресу отладки.|  
|`GetGlobalContainer`|Не рекомендуется. Не используется.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Получает поле, представляющее полному имени метода.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Получает тип поля класса, представляющий полное имя класса.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Создает перечислитель для пространств имен, связанный с адресом отладки.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Имя символа сопоставляется тип символа.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Возвращает адрес отладки, следующий за адресом заданной отладочной в методе.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс сопоставляет позиции документа в адреса отладки и наоборот.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
 В этом примере показано, как создать экземпляр поставщика символов, учитывая его идентификатора GUID (модуля отладки необходимо знать, это значение).  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
