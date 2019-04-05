---
title: IDiaEnumSymbols | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e41cec8cf40195e7156b0515c1aa1a7502e3a03f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990520"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перечисляет различные символов, содержащихся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumSymbols`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Извлекает `IEnumVARIANT Interface` версии этот перечислитель.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Возвращает число символов.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Получает символ с помощью индекса.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Извлекает указанное число символов в последовательности перечисления.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Пропускает заданное число символов в последовательности перечисления.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс предоставляет символы, сгруппированные по определенный тип символа, например, `SymTagUDT` (определяемые пользователем типы) или `SymTagBaseClass`. Для работы с символами, сгруппированными по адресам используйте [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Для получения этого интерфейса вызов следующих методов:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaEnumSymbols` интерфейс, а затем использовать это перечисление, чтобы список определяемых пользователем типов (UDT).  
  
> [!NOTE]
>  `CDiaBSTR` — Это класс, который заключает в оболочку `BSTR` и автоматически обрабатывает освобождение строки, когда экземпляр выходит из области.  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (пакет SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
