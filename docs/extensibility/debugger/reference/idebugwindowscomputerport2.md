---
title: IDebugWindowsComputerPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9126d7507f47852b7fc9bcd3777b112932892bb4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702152"
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

|Метод|Описание:|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Извлекает сведения о компьютере, на котором выполняется отладчик.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll