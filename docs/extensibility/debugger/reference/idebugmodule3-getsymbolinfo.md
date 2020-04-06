---
title: IDebugModule3::GetSymbolInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726900"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Извлекает список путей, которые ищут символы, а также результаты поиска каждого пути.

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

## <a name="parameters"></a>Параметры
`dwFields`\
(в) Комбинация флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисления с `pInfo` указанием, какие поля должны быть заполнены.

`pInfo`\
(ваут) [Структура MODULE_SYMBOL_SEARCH_INFO,](../../../extensibility/debugger/reference/module-symbol-search-info.md) члены которой должны быть заполнены указанной информацией. Если это нулевая величина, этот метод возвращается. `E_INVALIDARG`

## <a name="return-value"></a>Возвращаемое значение
Если метод удается, `S_OK`он возвращается ; в противном случае он возвращает код ошибки.

> [!NOTE]
> Верная строка `MODULE_SYMBOL_SEARCH_INFO` (в структуре) `S_OK` может быть пустой, даже если она возвращается. В этом случае, не было никакой поисковой информации, чтобы вернуться.

## <a name="remarks"></a>Примечания
Если `bstrVerboseSearchInfo` поле `MODULE_SYMBOL_SEARCH_INFO` структуры не пусто, то оно содержит список поисковых путей и результаты этого поиска. Список отформатирован с помощью пути, за которым следует эллипсис ("..."), за которым следует результат. Если есть более чем одна пара результатов пути, то каждая пара отделяется парой «Зран» (перевозка-возврат/линия). Шаблон выглядит следующим образом:

\<путь>... \<результат>\<> пути... \<результат>\<пути>... \<результат>

Обратите внимание, что последняя запись не имеет последовательности крюн.

## <a name="example"></a>Пример
В этом примере этот метод возвращает три пути с тремя различными результатами поиска. Каждая строка прекращается парой перевозки-возврата/линейного питания. Вывод примера просто печатает результаты поиска как одну строку.

> [!NOTE]
> Статус результат все сразу же после "..." до конца строки.

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

**c: «символы»user32.pdb... Файл не найден.** 
 **c: «Виннент»-символы-user32.pdb... Версия не совпадает.** 
 ** \\«Символы»-символы»user32.dll»0a8sd0ad8ad»user32.pdb... Символы загружены.**

## <a name="see-also"></a>См. также

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
