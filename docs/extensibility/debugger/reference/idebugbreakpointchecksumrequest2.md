---
title: IDebugBreakpointChecksumRequest2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfad0d8469a3cd01b5697cd9ba74f7a84ee84b83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923394"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Представляет контрольную сумму документа для запроса точки останова.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализованный [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пакет отладки и используемый отладчиков.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugBreakpointChecksumRequest2`.

|Метод|Описание|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Извлекает контрольная сумма документа для запроса точки останова Получает уникальный идентификатор алгоритма подсчета контрольной суммы для использования.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Определяет, включена ли контрольная сумма для этого документа.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll