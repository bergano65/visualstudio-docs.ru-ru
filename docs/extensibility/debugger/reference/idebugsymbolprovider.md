---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "Интерфейс IDebugSymbolProvider"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет поставщик, предоставляющий символы и типы символов, возвращая их как поля.  
  
## Синтаксис  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## Примечания по реализации  
 Поставщик символов, должен реализовать этот интерфейс, чтобы указать символ и сведения о типе к средству оценки выражений.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс можно получить с помощью модели COM `CoCreateInstance` функция \(для неуправляемых поставщиков символов\) или путем загрузки соответствующую сборку управляемого кода и создание экземпляра поставщика символов на основе сведений найдено в этой сборке.  Создает обработчика отладки поставщика символа, который требуется работать в координации со средством оценки выражений.  См. пример для одного подхода к того, этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugSymbolProvider`.  
  
|Метод|Описание|  
|-----------|--------------|  
|`Initialize`|Устаревший.  Не используется.|  
|`Uninitialize`|Устаревший.  Не используется.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Возвращает поле, содержащее адрес отладки.|  
|`GetField`|Устаревший.  Не используется.|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|Сопоставляет позиции документа в массив адресов отладки.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Сопоставляет контекст рисования в массив адресов отладки.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Сопоставляет адреса отладки в контекст рисования.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Возвращает язык, используемый компилировать код по адресу отладки.|  
|`GetGlobalContainer`|Устаревший.  Не используется.|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|Возвращает поле, представляющее полное имя метода.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Получает тип поля класса, представляющего полное имя класса.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Создает перечислитель для пространств имен, связанных с адресом отладки.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Сопоставляет имя символа в тип символа.|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|Возвращает адрес отладки, который следует за заданным адресом отладки в методе.|  
  
## Заметки  
 Этот интерфейс сопоставляет позиции документа в отладочной адреса и наоборот.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Пример  
 В этом примере показано, как создать экземпляр поставщика символов, задавая его GUID \(отладчик должен знать это значение\).  
  
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
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)