---
title: IDebugСправка2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720263"
---
# <a name="idebugreference2"></a>IDebugReference2
Этот интерфейс представляет собой отсылку к свойству кадра стека или другому свойству.

> [!NOTE]
> `IDebugReference2`зарезервирован для использования в будущем, и `E_NOTIMPL`все его методы должны вернуться.

## <a name="syntax"></a>Синтаксис

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы представлять ссылку на определенный вид значения. Например, значение может быть числовым значением в результате оценки выражения, контекстом памяти, используемым для отображения памяти, или списком регистров и их значений.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [GetReference,](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) чтобы получить этот интерфейс. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) и [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) также вернуть этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugReference2`.

|Метод|Описание|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Получает [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуру, описываемую эту ссылку.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Устанавливает значение этой ссылки из строки.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Устанавливает значение этой ссылки из другой ссылки.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Перечисляет детей этой ссылки.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Получает родитель этой ссылки.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Получает наиболее производные ссылки на эту ссылку.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Получает байты памяти, к которым ссылается эта ссылка.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Получает контекст памяти для этой ссылки.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Получает размер, в байтах, этой ссылки.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Устанавливает этот тип ссылки.|
|[Сравнить](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Сравнивает эту ссылку с другой.|

## <a name="remarks"></a>Примечания

> [!NOTE]
> Такое использование "имущества" не следует путать с тем, что `IDebugReference2` означает переменную члена класса, хотя может представлять такую сущность.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) представляет свойство, в то время как `IDebugReference2` представляет собой ссылку на свойство, как правило, ссылка на объект в программе отладки.

 Основное различие между свойством и ссылкой состоит в том, что свойство относится к названному экземпляру объекта, в то время как ссылка относится к неназванному экземпляру. Например, свойство может относиться к объекту в `"a.b"`куче программы по способом . Другое свойство может относиться к тому же объекту, что и `"c.d"`. Способ ссылки на это `"a.b"` свойство требует этого или `"c.d"` быть в области. Ссылка на этот же объект безымяна; объект может быть отнесен к до тех пор, пока память для этого объекта действительна.

 Интерфейс `IDebugProperty2` можно рассматривать как значение с именем, типом и адресом. `IDebugReference2`An, с другой стороны, можно рассматривать как тип и адрес.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
