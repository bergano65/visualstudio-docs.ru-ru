---
title: IDebugModOpt | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1bbfbc6b6e567e0e56aa369f9c0d1f13a4cbe34
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690933"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Представляет необязательный модификатор отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Полученный из [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, который представляет собой класс или метод.

## <a name="methods"></a>Методы
 Этот интерфейс реализует следующий метод:

|Метод|Описание:|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Возвращает список необязательных модификаторов.|

## <a name="requirements"></a>Требования
 Заголовок: Sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll