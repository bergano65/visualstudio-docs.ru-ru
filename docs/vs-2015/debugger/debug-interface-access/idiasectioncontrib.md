---
title: IDiaSectionContrib | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5128059cfeac1c30d392c7122ee458ac9a84240
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562641"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSectionContrib](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasectioncontrib).  
  
Извлекает данные, описывающие вклад раздела, то есть непрерывный блок памяти порожденного к образу единице компиляции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaSectionContrib`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Извлекает ссылку на символ компилируемого объекта, который участвует в этом разделе.|  
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Извлекает раздел часть адреса вклада.|  
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Извлекает часть смещения вклад адреса.|  
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|Извлекает изображение относительный виртуальный адрес (RVA) вклад.|  
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Получает виртуальный адрес (VA) вклада.|  
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Возвращает число байтов в разделе.|  
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Получает флаг, указывающий, может ли быть оповещен разделе не хватает памяти.|  
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Получает флаг, указывающее, является ли раздел не будут заполнены до следующей границы памяти.|  
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|Получает флаг, указывающий, содержит ли раздел исполняемый код.|  
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Получает флаг, указывающий, содержит ли раздел 16-разрядного кода.|  
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Получает флаг, указывающий, содержит ли раздел инициализированные данные.|  
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|Получает флаг, указывающий, содержит ли раздел неинициализированных данных.|  
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Получает флаг, указывающий, содержит ли раздел комментарии или аналогичные сведения.|  
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Получает флаг, указывающий, удален ли раздел, прежде чем оно станет изображением в памяти.|  
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Получает флаг, указывающий, является ли раздел записи COMDAT.|  
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Получает флаг, указывающий, могут быть удалены разделе.|  
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Получает флаг, указывающий ли раздел не может быть кэширован.|  
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Получает флаг, указывающий, могут ли разделе совместно в памяти.|  
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Получает флаг, указывающий, является ли раздел исполняемого файла, как код.|  
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Получает флаг, указывающий, может ли быть прочитан разделе.|  
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Получает флаг, указывающий, можно ли выполнять запись раздела.|  
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Извлекает циклическую проверку избыточности (CRC) данных в разделе.|  
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Возвращает контрольную СУММУ для области данных перемещение.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Извлекает идентификатор для раздела единице компиляции.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс получается путем вызова [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) и [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) методы. См. в разделе [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) интерфейс пример получения `IDiaSectionContrib` интерфейс.  
  
## <a name="example"></a>Пример  
 Эта функция показывает адрес каждого раздела, а также все связанные символы. См. в разделе [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) для просмотра как `IDiaSectionContrib` интерфейс получается.  
  
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
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)



