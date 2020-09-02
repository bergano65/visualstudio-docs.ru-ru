---
title: IDiaSegment | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe9586797c334afb60f60311963dc2df72fdad5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151725"
---
# <a name="idiasegment"></a>IDiaSegment
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Сопоставляет данные из номера раздела с сегментами адресного пространства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSegment : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaSegment` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Извлекает номер сегмента.|  
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Возвращает смещение в сегментах, где начинается раздел.|  
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Возвращает число байтов в сегменте.|  
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Получает флаг, указывающий, можно ли считать сегмент.|  
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Получает флаг, указывающий, можно ли изменить сегмент.|  
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Получает флаг, указывающий, является ли сегмент исполняемым.|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Извлекает номер раздела, который сопоставляется с этим сегментом.|  
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Извлекает относительный виртуальный адрес (RVA) начала раздела.|  
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Получает виртуальный адрес (ва) начала раздела.|  
  
## <a name="remarks"></a>Remarks  
 Так как пакет SDK для DIA уже выполняет переводы из смещения раздела в относительные виртуальные адреса, большинство приложений не будет использовать информацию на карте сегментов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получите этот интерфейс, вызвав методы [идиаенумсегментс:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) или [Идиаенумсегментс:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) . Дополнительные сведения см. в примере.  
  
## <a name="example"></a>Пример  
 Эта функция отображает адрес всех сегментов в таблице и ближайший символ.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
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
 [Идиаенумсегментс:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
