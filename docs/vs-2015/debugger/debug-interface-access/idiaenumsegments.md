---
title: IDiaEnumSegments | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45ab7bdf76cf169fbc2eee6669771a95ff767006
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990530"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Перечисляет различные сегменты, содержащихся в источнике данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaEnumSegments`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Извлекает [интерфейса IEnumVARIANT](http://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) версии этот перечислитель.|  
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Извлекает число сегментов.|  
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Возвращает сегмент с помощью индекса.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Возвращает указанное количество сегментов в последовательности перечисления.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Пропускает заданное число сегментов в последовательности перечисления.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Получить этот интерфейс, вызвав `QueryInterface` метод [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объекта. Дополнительные сведения см.  
  
## <a name="example"></a>Пример  
 В этом примере показано, как получить `IDiaEnumSections` интерфейс из таблицы. Более полный пример использования сегменты, см. в разделе [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) интерфейс.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (пакет SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
