---
title: IDiaSectionContrib | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc263d7238166f4f381bac35f0482ca2433f7b33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150482"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает данные, описывающие вклад раздела, то есть непрерывный блок памяти, внесенный в изображение с помощью компилируемого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaSectionContrib` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Извлекает ссылку на символ компилируемого объекта, который участвует в этом разделе.|  
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Извлекает часть адреса вклада в раздел.|  
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Извлекает смещение адреса вклада.|  
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Возвращает относительный виртуальный адрес (RVA) образа публикации.|  
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Извлекает виртуальный адрес (ва) публикации.|  
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Возвращает число байтов в разделе.|  
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Получает флаг, указывающий, что раздел не может быть выводится из памяти.|  
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Получает флаг, указывающий, должен ли раздел быть заполнен до следующей границы памяти.|  
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Получает флаг, указывающий, содержит ли раздел исполняемый код.|  
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Получает флаг, указывающий, содержит ли раздел 16-разрядный код.|  
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Получает флаг, указывающий, содержит ли раздел инициализированные данные.|  
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Получает флаг, указывающий, содержит ли раздел неинициализированные данные.|  
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Получает флаг, указывающий, содержит ли раздел комментарии или похожие сведения.|  
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Получает флаг, указывающий, удаляется ли раздел до того, как он станет частью изображения в памяти.|  
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Получает флаг, указывающий, является ли раздел записью типа COMDAT.|  
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Получает флаг, указывающий, можно ли отменять раздел.|  
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Получает флаг, указывающий, не удается ли кэшировать раздел.|  
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Получает флаг, указывающий, может ли раздел быть общим в памяти.|  
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Получает флаг, указывающий, является ли раздел исполняемым кодом.|  
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Получает флаг, указывающий, можно ли прочитать раздел.|  
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Получает флаг, указывающий, можно ли записать раздел.|  
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Извлекает циклическую проверку избыточности (CRC) данных в разделе.|  
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Извлекает контрольную сумму для сведений о перерасположении раздела.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Возвращает идентификатор компилируемого объекта для раздела.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс получается путем вызова методов [идиаенумсектионконтрибс:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) и [Идиаенумсектионконтрибс:: Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) . Пример получения интерфейса см. в интерфейсе [идиаенумсектионконтрибс](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) `IDiaSectionContrib` .  
  
## <a name="example"></a>Пример  
 Эта функция отображает адрес каждого раздела вместе со всеми связанными символами. Сведения о получении интерфейса см. в интерфейсе [идиаенумсектионконтрибс](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) `IDiaSectionContrib` .  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [идиаенумсектионконтрибс](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [Идиаенумсектионконтрибс:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
