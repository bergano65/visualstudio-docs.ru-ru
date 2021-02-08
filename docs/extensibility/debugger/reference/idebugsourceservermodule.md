---
title: Идебугсаурцесервермодуле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dfc4b3defc0b74c1e22c45670209682692a4807
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837701"
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
