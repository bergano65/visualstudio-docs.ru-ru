---
title: IDebugCustomAttribute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 338f07f26bf4d0471fbf178a369a085d5ef76a08
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679090"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Этот интерфейс представляет настраиваемый атрибут, и это может дать имя, родительский и тип класса атрибута.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс для поддержки настраиваемые атрибуты, связанные с символом. Как правило, он реализован в свой собственный объект.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызов [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает этот интерфейс. Вызов [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCustomAttribute`.

|Метод|Описание|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Получает поле, к которой подключен текущий атрибут.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Возвращает тип класса настраиваемого атрибута.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Получает имя настраиваемого атрибута.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Возвращает сведения об атрибутах как большой двоичный объект байтов.|

## <a name="remarks"></a>Примечания
 Настраиваемый атрибут представляет собой структуру для C#, который предоставляет пользовательские метаданные, связанные с определенным классом или методом.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)