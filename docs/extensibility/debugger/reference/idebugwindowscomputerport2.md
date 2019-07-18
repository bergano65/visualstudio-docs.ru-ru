---
title: IDebugWindowsComputerPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2a60572c652080f2655ab7fe33954a661fbe07e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319743"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Позволяет запрашивать сведения о конечном компьютере.

## <a name="syntax"></a>Синтаксис

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется объектами порта диспетчера сеанса отладки.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugWindowsComputerPort2`.

|Метод|Описание|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Извлекает сведения о компьютере, на котором выполняется отладчик.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll