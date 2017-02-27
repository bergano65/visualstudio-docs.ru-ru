---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "Метод GetSymbolInfo"
  - "Метод IDebugModule3::GetSymbolInfo"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает список путей, в которых производится поиск символов, а также результаты поиска каждого пути.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### Параметры  
 `dwFields`  
 \[in\] Сочетание флагов из [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисление, определяющее, какие поля `pInfo` должны быть заполнены.  
  
 `pInfo`  
 \[out\] A [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) структуры, члены которой должны быть заполнены с использованием указанных сведений об. Если это значение null, этот метод возвращает `E_INVALIDARG`.  
  
## Возвращаемое значение  
 Если метод завершается успешно, возвращается `S_OK`; в противном случае возвращается код ошибки.  
  
> [!NOTE]
>  Возвращаемая строка \(в `MODULE_SYMBOL_SEARCH_INFO` структуры\) может быть пустым даже в том случае, если `S_OK` возвращается. В этом случае отсутствовали данные поиска для возврата.  
  
## Заметки  
 Если `bstrVerboseSearchInfo` поле `MODULE_SYMBOL_SEARCH_INFO` Структура не является пустым, то он содержит список пути поиска и результаты поиска. Список имеет формат с путем, а затем многоточие \(«...»\), а затем результат. Если имеется несколько пар результирующий путь, каждая пара отделяется пару «\\r\\n» \(каретки возврата и перевода строки\). Шаблон выглядит следующим образом:  
  
 \\r\\n \< путь \>... \< результат \> \< путь \>... \< результат \> \\r\\n \< путь \>... \< результат \>  
  
 Обратите внимание, что последний элемент последовательности \\r\\n.  
  
## Пример  
 В этом примере этот метод возвращает три пути с помощью трех разные результаты. Каждая строка завершается парой каретки возврата и перевода строки. Пример выходных данных просто выводит результаты поиска в одну строку.  
  
> [!NOTE]
>  Результат состояния является все, что сразу после «...» до конца строки.  
  
```cpp#  
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
  
 **c:\\symbols\\user32.PDB... Файл не найден. c:\\winnt\\symbols\\user32.PDB... Версия не совпадает. \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.PDB... Загрузить символы.**   
## См. также  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)