---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "Интерфейс IDebugReference2"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет ссылку на свойство кадра стека или другие свойства.  
  
> [!NOTE]
>  `IDebugReference2` зарезервировано для будущего использования, и его методы должны возвращать  `E_NOTIMPL`.  
  
## Синтаксис  
  
```  
IDebugReference2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализует этот интерфейс для представления ссылки на определенный тип значения.  Например, значение может быть по числовому значением в результате оценки выражений, контекст памяти, используемого для отображения памяти или списка регистров и их значений.  
  
## Замечания для вызывающих объектов  
 Вызов [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) получить этот интерфейс.  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) и [GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md) также возвращают этот интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugReference2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Возвращает [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структура, описывающая эту ссылку.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Устанавливает значение этой ссылки из строки.|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|Устанавливает значение этой ссылки из другой ссылки.|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|Перечисляет дочерние элементы данной ссылки.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Возвращает родительский объект для этой ссылки.|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|Возвращает более всего\-выведенную ссылку этой ссылки.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Возвращает объем памяти, на которые ссылается эта ссылка.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Возвращает контекст памяти для этой ссылки.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Возвращает размер \(в байтах\) этой ссылки.|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|Устанавливает этот ссылочный тип.|  
|[Сравнение](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Сравнивает эту ссылку с другими.|  
  
## Заметки  
  
> [!NOTE]
>  Эта использование "свойства" не следует путать с этой переменной члена класса, хотя смыслью `IDebugReference2` может представлять ту сущность.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) представляет свойство, пока `IDebugReference2` представляет ссылку на свойство, обычно ссылка на объект, отлаживанными в программе.  
  
 Основное различие между свойством и ссылкой, что свойство относится к именованному экземпляру объекта, а ссылка указывает на неименованный экземпляр.  Например, оно может ссылаться на объект в куче программы by `"a.b"`.  Другое свойство может относиться к одному и тому же объекту как `"c.d"`.  Способ обратившись к этому свойству, чтобы требует `"a.b"` OR  `"c.d"` в области.  Ссылка на данный один и тот же объект безыменна; объект можно ссылаться, если память для объекта допустимой.  
  
 `IDebugProperty2` интерфейс можно рассматривать как значения с именем, типом и адресом.  `IDebugReference2`с другой стороны, можно рассматривать в качестве типа и адреса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)