---
title: "IDiaStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame - интерфейс"
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# IDiaStackFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Предоставляет свойства кадра стека.  
  
## Синтаксис  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## Методы в том порядке Vtable  
 Следующие методы, поддерживаемые этим интерфейсом.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaStackFrame::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Извлекает пометить указывающее, что базовый указатель установлен для кода в этом диапазоне адресов.  Этот метод является устаревшим.|  
|[IDiaStackFrame::get\_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Получает базовый адрес кадра.|  
|[IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)|Извлекает пометить показывающее, что обработка исключений С\+\+.|  
|[IDiaStackFrame::get\_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Извлекает пометить указывающее, что блок содержит точку входа функции.|  
|[IDiaStackFrame::get\_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Извлекает число байтов локальных переменных отправлянных в стеке.|  
|[IDiaStackFrame::get\_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Возвращает число байтов отправлянных параметров в стеке.|  
|[IDiaStackFrame::get\_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Извлекает число байтов в блоке кода в прологе|  
|[IDiaStackFrame::get\_lengthSavedRegisters](../Topic/IDiaStackFrame::get_lengthSavedRegisters.md)|Извлекает число байт, сохраненных регистров отправлянных в стеке.|  
|[IDiaStackFrame::get\_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Получает базовый адрес локальные переменные.|  
|[IDiaStackFrame::get\_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Получает максимальное число байтов отправлянных в стеке во фрейме.|  
|[IDiaStackFrame::get\_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Получает значение заданной локальной переменной в виде необработанных байт.|  
|[IDiaStackFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Извлекает значение указанного регистра.|  
|[IDiaStackFrame::get\_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Получает обратный адрес кадра.|  
|[IDiaStackFrame::get\_size](../Topic/IDiaStackFrame::get_size.md)|Извлекает размер кадра, в байтах.|  
|[IDiaStackFrame::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Извлекает пометить показывающее, что обработка ошибок системы.|  
|[IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Извлекает тип кадра.|  
  
## Заметки  
 Абстракция кадр стека вызова функции во время его выполнения.  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) метод.  См. [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) интерфейс пример на получение  `IDiaStackFrame` интерфейс.  
  
## Пример  
 В этом примере показаны различные атрибуты кадра стека.  
  
```cpp#  
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
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)