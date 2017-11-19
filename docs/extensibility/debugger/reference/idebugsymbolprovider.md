---
title: "IDebugSymbolProvider | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider
helpviewer_keywords: IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33958c7159c6348aca696e295deb245031e904d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Этот интерфейс представляет поставщик символ, который предоставляет типы, возвращая их в виде полей и символы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик должен реализовывать этот интерфейс для предоставления символа и сведения о типе для вычислитель выражений.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс можно получить с помощью COM `CoCreateInstance` функция (для неуправляемого символ поставщики) или путем загрузки соответствующего управляемого кода сборки и создание экземпляра поставщика символа, на основе данных, находящиеся в этой сборке. Отладчик создает экземпляр поставщика символов для работы совместно с средство оценки выражений. Далее приведен пример одним из подходов для создания экземпляра этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugSymbolProvider`.  
  
|Метод|Описание|  
|------------|-----------------|  
|`Initialize`|Не рекомендуется. Не используется.|  
|`Uninitialize`|Не рекомендуется. Не используется.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Возвращает поле, содержащее адрес отладки.|  
|`GetField`|Не рекомендуется. Не используется.|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Сопоставляет позицию документа в массив адресов отладки.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Сопоставляет массив адресов отладки к контексту документа.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Сопоставляет адрес отладки в контексте документа.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Возвращает язык, используемый для компиляции кода по адресу отладки.|  
|`GetGlobalContainer`|Не рекомендуется. Не используется.|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Возвращает поле, представляющее имя полного имени метода.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Возвращает тип поля класса, представляющая полное имя класса.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Создает перечислитель для пространств имен, связанный с адресом отладки.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Сопоставляет имя символа типа символа.|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Возвращает адрес отладки, следующий адрес данного отладки в методе.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс сопоставляет позиции документа в адресов отладки и наоборот.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
 В этом примере показано создание экземпляра поставщика символа, учитывая его GUID (модуля отладки необходимо знать, это значение).  
  
```cpp  
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