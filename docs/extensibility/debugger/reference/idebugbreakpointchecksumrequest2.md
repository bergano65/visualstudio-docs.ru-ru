---
title: IDebugBreakpointChecksumRequest2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735124"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Представляет проверку документов для запроса точки разрыва.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Реализован пакетом [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debug и потребляется двигателями отладки.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugBreakpointChecksumRequest2`.

|Метод|Описание|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Извлекает проверку документа для запроса точки разрыва с учетом уникального идентификатора алгоритма проверки для использования.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Определяет, включена ли проверка для этого документа.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
