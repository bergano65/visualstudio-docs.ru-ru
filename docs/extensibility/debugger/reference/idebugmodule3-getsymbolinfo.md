---
title: IDebugModule3::GetSymbolInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fb03186d623c63fd4c3ff950140918244397115
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945760"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Извлекает список путей, для которых выполняется поиск символов, а также результаты поиска каждого пути.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 [in] Сочетание флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисление, определяющее, какие поля `pInfo` должны быть заполнены.  
  
 `pInfo`  
 [out] Объект [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) структуры, члены которого должны быть заполнены с использованием указанных сведений об. Если это значение null, этот метод возвращает `E_INVALIDARG`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается успешно, возвращается `S_OK`; в противном случае он возвращает код ошибки.  
  
> [!NOTE]
>  Возвращаемая строка (в `MODULE_SYMBOL_SEARCH_INFO` структуры) могут быть пустыми даже в том случае, если `S_OK` возвращается. В этом случае отсутствуют сведения поиска для возврата.  
  
## <a name="remarks"></a>Примечания  
 Если `bstrVerboseSearchInfo` поле `MODULE_SYMBOL_SEARCH_INFO` структура не является пустым, то он содержит список пути поиска и результаты поиска. Список форматируется с путем, последующим многоточием («...»), а затем результат. Если имеется несколько пар результирующий путь, каждая пара отделяется пару «\r\n» (каретки возврата и перевода строки). Шаблон выглядит следующим образом:  
  
 \<путь >... \<результат > \r\n\<путь >... \<результат > \r\n\<путь >... \<результата >  
  
 Обратите внимание, что последний элемент последовательности \r\n.  
  
## <a name="example"></a>Пример  
 В этом примере этот метод возвращает три пути с три разные результаты. Каждая строка завершается парой каретки возврата и перевода строки. В примере выходных данных просто выводит результаты поиска в одну строку.  
  
> [!NOTE]
>  Результат состояния — это все, что сразу после «...» до конца строки.  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.PDB... Файл не найден.**  
**c:\winnt\symbols\user32.PDB... Версия не совпадает.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.PDB... Символы загружены.**   
## <a name="see-also"></a>См. также  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)