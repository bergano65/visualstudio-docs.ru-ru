---
title: IDiaSourceFile | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8876febdae25c38d7cb637092d80dcac87f2418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190616"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Представляет исходный файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaSourceFile` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Возвращает простое значение целочисленного ключа, которое является уникальным для этого образа.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Извлекает имя исходного файла.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Возвращает тип контрольной суммы.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Извлекает перечислитель компиляндов с номерами строк, ссылающимися на этот файл.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Получает байты контрольной суммы.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получите этот интерфейс, вызвав методы [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) или [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) . Дополнительные сведения см. в примере.  
  
## <a name="example"></a>Пример  
 Эта функция отображает имена всех исходных файлов, участвующих в указанной таблице.  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
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
 [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber:: get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [IDiaSession:: Финдфилебид](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession:: Финдлинес](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
