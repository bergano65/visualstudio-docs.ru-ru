---
title: IDebugPortPicker | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340368"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Представляет настраиваемый пользовательский Интерфейс для выбора порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщикам портов. Поставщика порта определяет их выбора порта предоставлением в качестве идентификатора класса CLSID, и выберите пункт `metricPortPickerCLSID` метрик в предоставленный идентификатор CLSID.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortPicker`.

|Метод|Описание|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанный диалоговое окно, которое позволяет пользователю выбрать порт.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик службы.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll