---
title: "IDiaEnumSymbols | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 372279d82f9f316edf0d1aed203be1ce4e48e236
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
Перечисляет различные символов, содержащихся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumSymbols`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Извлекает `IEnumVARIANT Interface` версии этот перечислитель.|  
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Возвращает число символов.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Возвращает символ с помощью индекса.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Возвращает указанное число символов в последовательность перечисления.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Пропускает указанное число символов в последовательность перечисления.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Сбрасывает последовательность перечисления в начало.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Создает перечислитель, с тем же состоянием, как у текущего перечислителя.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс предоставляет символы, сгруппированные по определенный тип символа, например, `SymTagUDT` (определяемые пользователем типы) или `SymTagBaseClass`. Для работы с символами, сгруппированные по адресу, используйте [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получите этот интерфейс путем вызова следующих методов:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaEnumSymbols` интерфейс, а затем с помощью этого перечисления список определяемых пользователем типов (UDT).  
  
> [!NOTE]
>  `CDiaBSTR`Представляет класс-оболочку `BSTR` и автоматически обрабатывает освобождая строку, когда экземпляр выходит за пределы области.  
  
```C++  
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
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)