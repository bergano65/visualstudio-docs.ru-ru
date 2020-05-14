---
title: IDebugModOpt Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726972"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Представляет собой отладку опциональном модификатором.

## <a name="syntax"></a>Синтаксис

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Заметки для абонентов
 Получено с объекта [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющего класс или метод.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Извлекает список дополнительных модификаторов.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
