---
title: IDebugCodeКонтекст3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734190"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Расширяет интерфейс [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) чтобы обеспечить поиск интерфейсов модуля и процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Реализовано путем отладки [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] двигателей и потребляется пакетом Debug.

## <a name="methods"></a>Методы
 В дополнение к методам `IDebugCodeContext2` на интерфейсе, этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Извлекает ссылку на интерфейс модуля отладки.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Извлекает ссылку на интерфейс процесса отладки.|

## <a name="remarks"></a>Примечания
 Это дополнительный интерфейс, который, как правило, не должны быть реализованы.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
