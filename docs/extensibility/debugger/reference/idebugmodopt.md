---
title: Идебугмодопт | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aff72199b6b79f2cca30e99533311ac617816b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941779"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Представляет необязательный модификатор отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Получен из объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющего класс или метод.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Извлекает список необязательных модификаторов.|

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
