---
title: IDiaStackFrame | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 520c1d566cb133ceb839848eb3df229380468807
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackframe"></a>IDiaStackFrame
Предоставляет свойства кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Ниже приведены методы, поддерживаемые этим интерфейсом.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Возвращает флаг, указывающий, что базового указателя выделяется для кода в этом диапазоне. Этот метод является устаревшим.|  
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Получает базовый адрес кадра.|  
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Возвращает флаг, указывающий, что обработка исключений с ++ действует.|  
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Возвращает флаг, указывающий, что блок содержит точку входа функции.|  
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Возвращает число байтов, локальных переменных в стек.|  
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Возвращает число байтов параметров в стек.|  
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Возвращает число байтов кода пролога в блоке|  
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Возвращает число байтов, сохраненных регистров в стек.|  
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Получает базовый адрес локальных переменных.|  
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Возвращает максимальное число байтов, помещаются в стек в кадре.|  
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Получает значение указанной локальной переменной в виде необработанных байтов.|  
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Получает значение указанного регистра.|  
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Возвращает обратный адрес кадра.|  
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Получает размер кадра, в байтах.|  
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Возвращает флаг, указывающий, что обработка исключений системы действует.|  
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Получает тип пакета.|  
  
## <a name="remarks"></a>Примечания  
 Кадр стека представляет собой абстракцию вызов функции во время выполнения.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Получить этот интерфейс, вызвав [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) метод. В разделе [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) интерфейс пример получения `IDiaStackFrame` интерфейса.  
  
## <a name="example"></a>Пример  
 Этот пример отображает различные атрибуты кадра стека.  
  
```C++  
void PrintStackFrame(IDiaStackFrame* pFrame)  
{  
    if (pFrame != NULL)  
    {  
        ULONGLONG bottom = 0;  
        ULONGLONG top    = 0;  
  
        if (pFrame->get_base(&bottom) == S_OK &&  
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )  
        {  
             printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);  
        }  
  
        ULONGLONG returnAddress = 0;  
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)  
        {  
             printf("return address = 0x%08I64x\n", returnAddress);  
        }  
  
        DWORD lengthFrame     = 0;  
        DWORD lengthLocals    = 0;  
        DWORD lengthParams    = 0;  
        DWORD lengthProlog    = 0;  
        DWORD lengthSavedRegs = 0;  
        if (pFrame->get_size(&lengthFrame) == S_OK &&  
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&  
            pFrame->get_lengthParams(&lengthParams) == S_OK &&  
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&  
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)  
        {  
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);  
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);  
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);  
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);  
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);  
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
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)