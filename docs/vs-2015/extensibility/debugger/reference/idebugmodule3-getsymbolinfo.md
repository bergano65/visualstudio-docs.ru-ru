---
title: 'IDebugModule3:: Жетсимболинфо | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 48dd08b8ef1a8b32497d03dc7989b32a22ee5a9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843280"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает список путей, в которых выполняется поиск символов, а также результаты поиска по каждому пути.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Сочетание флагов из перечисления [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) , в котором указываются поля `pInfo` , которые должны быть заполнены.  
  
 `pInfo`  
 заполняет Структура [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) , члены которой должны быть заполнены указанной информацией. Если это значение равно null, этот метод возвращает `E_INVALIDARG` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается с ошибкой, возвращается `S_OK` значение; в противном случае возвращается код ошибки.  
  
> [!NOTE]
> Возвращаемая строка (в `MODULE_SYMBOL_SEARCH_INFO` структуре) может быть пустой даже при `S_OK` возвращении. В этом случае поисковые данные для возврата отсутствуют.  
  
## <a name="remarks"></a>Remarks  
 Если `bstrVerboseSearchInfo` поле `MODULE_SYMBOL_SEARCH_INFO` структуры не пусто, оно содержит список путей, в которых выполняется поиск, и результаты этого поиска. Список форматируется с помощью пути, за которым следует многоточие ("..."), за которым следует результат. Если существует несколько пар результатов пути, каждая пара отделяется парой "\r\n" (возврат каретки или перевод строки). Шаблон выглядит следующим образом:  
  
 \<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>  
  
 Обратите внимание, что последняя запись не содержит последовательность \r\n.  
  
## <a name="example"></a>Пример  
 В этом примере этот метод возвращает три пути с тремя разными результатами поиска. Каждая строка завершается парой символов возврата каретки и перевода строки. В примере OUTPUT результаты поиска выводятся в виде одной строки.  
  
> [!NOTE]
> Результат состояния — это все, что сразу после "..." до конца строки.  
  
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
  
 **c:\symbols\user32.pdb... Файл не найден.**  
**c:\winnt\symbols\user32.pdb... Версия не совпадает.**  
**\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Символы загружены.**   
## <a name="see-also"></a>См. также:  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
