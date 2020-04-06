---
title: IDebugSourceServerModule (англ.) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719910"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Представляет информацию об исходном сервере, содержащуюся в файле PDB.

## <a name="syntax"></a>Синтаксис

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован с помощью двигателей-отладчиков и потребляется uI-интерфейсом отладчика.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugSourceServerModule`.

|Метод|Описание|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив информации об исходном сервере.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
