---
title: Идебугсаурцесервермодуле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719910"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Представляет сведения о исходном сервере, содержащиеся в PDB-файле.

## <a name="syntax"></a>Синтаксис

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется механизмами отладчика и используется в пользовательском интерфейсе отладчика.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugSourceServerModule` .

|Метод|Описание|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив сведений о исходном сервере.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
